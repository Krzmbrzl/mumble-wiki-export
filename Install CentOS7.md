Installation of murmur server on CentOS 7 (RHEL 7) using the static mumble server.
## Install 
Download the static murmur server.  Then run the following commands to install:
<pre>
tar -vxjf ./murmur-static_x86-1.2.8.tar.bz2
sudo mkdir /usr/local/murmur
sudo cp -r ./murmur-static_x86-1.2.8/* /usr/local/murmur/
sudo cp ./murmur-static_x86-1.2.8/murmur.ini /etc/murmur.ini
</pre>
Now create the murmur user and group, data directory, and logging directory:
<pre>
sudo groupadd -r murmur
sudo useradd -r -g murmur -m -d /var/lib/murmur -s /sbin/nologin murmur
sudo mkdir /var/log/murmur
sudo chown murmur:murmur /var/log/murmur
sudo chmod 0770 /var/log/murmur
</pre>

## System Configuration 

### Murmur.ini 
Make sure that the following settings are configured correctly in /etc/murmur.ini:
<pre>
database=/var/lib/murmur/murmur.sqlite
logfile=/var/log/murmur/murmur.log
pidfile=/var/run/murmur/murmur.pid
# Reminder: When changing the port that murmur will listen to you will need to also update the firewall.
# Update the firewall by editing /etc/firewalld/services/murmur.xml
# Then run "sudo firewall-cmd --reload"
port=64738
# Comment out the following setting since the service will already be executing as the correct user:
# uname=murmur
</pre>

### Allow to run as a background process 
Create a systemd unit file so that the murmur service can be managed by the operating system.  Using your text editor of choice, create the file '/etc/systemd/system/murmur.service' (Requires root).  Copy and paste the following:
<pre>
[Unit]
Description=Mumble Server (Murmur)
Requires=network-online.target
After=network-online.target mariadb.service time-sync.target

[Service]
User=murmur
Type=forking
ExecStart=/usr/local/murmur/murmur.x86 -ini /etc/murmur.ini
PIDFile=/var/run/murmur/murmur.pid
ExecReload=/bin/kill -s HUP $MAINPID

[Install]
WantedBy=multi-user.target
</pre>

On modern systems /var/run is discarded after reboot.  To regenerate the pid directory for murmur, create the configuration file '/etc/tmpfiles.d/murmur.conf' as root and copy and paste:
<pre>
d /var/run/murmur 775 murmur murmur
</pre>

### Rotate logs 
Setup logrotate so that murmur logs do not fill /var/log up. Create the '/etc/logrotate.d/murmur' configuration file as root and copy and paste:
<pre>
/var/log/murmur/*log {
    su murmur murmur
    dateext
    rotate 4
    missingok
    notifempty
    sharedscripts
    delaycompress
    postrotate
        /bin/systemctl reload murmur.service > /dev/null 2>/dev/null || true
    endscript
}
</pre>


### Firewall 
Setup firewalld so that it allows the service to listen to TCP/UDP.  If you adjusted murmur.ini so that it listens to a non-default port, then you will need to change this step to reflect your modifications.  As root, create the configuration file '/etc/firewalld/services/murmur.xml' and copy and paste:
<pre>
<?xml version="1.0" encoding="utf-8"?>
<service>
        <short>Murmur</short>
        <description>Mumble Server (Murmur)</description>
        <port protocol="tcp" port="64738" /><!-- Reminder: Update /etc/murmur.ini so that it uses the same ports -->
        <port protocol="udp" port="64738" />
</service>
</pre>
Then add the firewall rule to the default zone and then reload:
<pre>
sudo firewall-cmd --permanent --add-service=murmur
sudo firewall-cmd --reload
</pre>

### SELinux 

'''Note''': SELinux does not seem to prevent murmur from functioning as of RHEL or CentOS 7.2+. Please try running murmur with SELinux in enforcing mode first. If in doubt, check for murmur-related AVC entries in '/var/log/audit/audit.log'.


'''Note''': The steps outlined here will probably make security folks cringe.  If anyone has the time and patience to figure out SELinux, please consider updating this document with a proper solution.

SELinux by default will prevent murmur from functioning correctly.  The quick and easy solution is to simply disable it.  To disable temporarily (until the next reboot), run:
<pre>
sudo setenforce 0
</pre>
To disable permanently (after the next reboot), edit '/etc/sysconfig/selinux' and change the "SELINUX" line to:
<pre>
SELINUX=disabled
</pre>

### Finishing up 
Update your system so that it is ready to start the murmur service:
<pre>
sudo systemd-tmpfiles --create /etc/tmpfiles.d/murmur.conf
sudo systemctl daemon-reload
</pre>
To temporarily start the murmur service (until the next reboot), run:
<pre>
sudo systemctl start murmur.service
</pre>
To tell the system to autostart the murmur service (this will NOT immediately start murmur, instead it will start on the next reboot):
<pre>
sudo systemctl enable murmur.service
</pre>

{{Warning
|message=If you get a zombie process when starting Murmur, you have to install the '''redhat-lsb-core''' package.
}}


