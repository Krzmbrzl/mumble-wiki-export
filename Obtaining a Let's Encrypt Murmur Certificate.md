Let’s Encrypt is a trusted Certificate Authority. Using a certificate signed/created by them will make your server "trusted" by default. Users will not have to manually accept the server certificate as trusted. To indicate these "strong" server certificates, such servers are marked green in the public server list and on the servers root channel.

Let's Encrypt provides a variety of ways how to get a certificate for your server for free but you must have a domain name you own. How to verify you own your domain depends on a high variety of factors. Please refer to the  [Encrypt](https://letsencrypt.org/getting-started/ official Getting Started documentation of Let’s). ( [guide](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04 This) for Ubuntu 16.04 and nginx by DigitalOcean may also be helpful.)

In short: You will verify that you own the domain by making a file accessible through HTTP at a specified URL according to the ACME protocol. Depending on your system and Webserver this can be automated without configuration, or automated with manual web configuration. After obtaining an initial certificate, it should be renewed regularly (through an automated process), before the current certificate expires.

In your ''mumble-server.ini'' configuration file you will have to set the ''sslCert'' and ''sslKey'' settings to point to the respective certificate files:

 # The files fullchain.pem and privkey.pem should be the ones in the certificate folder letsencrypt created.
 # The server needs to be restarted to load the new settings/certificates.
 sslCert='' [to](path)''/fullchain.pem
 sslKey='' [to](path)''/privkey.pem

The path (apart from the domain name) is likely to be:

 sslCert=/etc/letsencrypt/live/''mumble.example.com''/fullchain.pem
 sslKey=/etc/letsencrypt/live/''mumble.example.com''/privkey.pem
 

If your server fails to load the certificate files (due to insufficient permissions) it may be necessary to give directory execute permissions to the folders in the path ''/etc/letsencrypt/live/''mumble.example.com'' and ''/etc/letsencrypt/archive/''mumble.example.com'' for the server to be able to read the certificate files inside of them. The log warning message looks like this:

 ''<C> [time](date) Failed to read /etc/letsencrypt/live/mumble.example.org/cert.pem''

=Live Reloading of Certificates=

From Version 1.3.0 onwards (commit  [1742f8](https://github.com/mumble-voip/mumble/commit/1742f8698377b187a6dabc0047ab64e4ad00dc35)), SIGUSR1 can be used to reload SSL settings. So after you updated the Let’s Encrypt certificate you should call SIGUSR1 on the Mumble server process to make it load the new certificate.

Depending on your setup of automatic certificate renewal, this may look like this:

File ''/etc/cron.daily/letsencrypt''

 /opt/certbot/certbot-auto renew --quiet --post-hook "service nginx reload ; start-stop-daemon --quiet --oknodo --stop --signal 10 --pidfile /var/run/mumble-server/mumble-server.pid"


