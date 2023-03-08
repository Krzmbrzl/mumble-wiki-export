Mumble-Django is a Murmur web interface application for Django that configures a Mumble server. It is able to create and remove server instances, start/stop them, and configure them. Furthermore, registered Django users can sign up for user accounts on the configured vservers and change their registration names and passwords, and Django admins can manage server admins through the webinterface.


## Main features 

* Compatible with Murmur 1.1.4, 1.1.8 and 1.2.0 up to 1.2.3
*  [list](http://cdn.bitbucket.org/Svedrin/mumble-django/downloads/channel_list.jpg Public channel) for each configured server ( [Demo](http://shotgunfun.de/mumble/1/ view the))
* Create and delete Mumur instances on as many Murmur installations as you want, they just need to be on the System DBus / ICE
* Ships with a  [Munin](http://munin.projects.linpro.no/) plugin that graphs the user count for each registered server ( [Demo](http://munin.funzt-halt.net/funzt-halt.net/glint.funzt-halt.net/mumble_django.html view the))
* Edit many configuration details in the Admin Interface for a Murmur instance
* Murmur instances can be started/stopped directly from the web interface
* Fully supports the [[Channel Viewer Protocol]]
* User registration
*  [interface](http://cdn.bitbucket.org/Svedrin/mumble-django/downloads/murmur_admin_website.jpg Admin) for server admins to configure basic settings
* handling user textures
* an Ice connector to allow simple switching between DBus and Ice
* Main template is a single file: if you don't like the look-and-feel, just change index.htm
* Extensibility: Being a standard Django project and using standard Django Models, you can extend Mumble-Django easily and build a complete website around it.

## Download 

You can download Mumble-Django either by getting a snapshot  [page](http://mumble-django.org/bb/downloads/ from the download) or by checking out from the Mercurial repo with the following command:
 hg clone https://bitbucket.org/Svedrin/mumble-django/

## Debian/Ubuntu 

I'm packaging Mumble-Django for Debian, and Ubuntu has merged the packages. The earliest stable releases that include MD are Debian Squeeze and Lucid Lynx.

{{Notice
|message=The packages included in Ubuntu Lucid Lynx have an error in their configuration file. The variable SLICE_VERSION needs to be changed to (1, 2, 2) before Mumble-Django will work.
}}

##Installation

Detailed installation instructions are available on the  [website](http://mumble-django.org/ Main), both in  [English](http://mumble-django.org/docs/en/installation.html) and  [German](http://mumble-django.org/docs/de/installation.html).

###Ubuntu 10.10
;Step 1 - Install
 sudo apt-get install mumble-django

;Step 2 - Configure
 sudo mumble-django-configure

;Step 3 - Administrate
 http://localhost/mumble-django

##Troubleshooting
###Ubuntu
;Python errors
if:
 $ python manage.py syncdb

yields:
 $ Error: No module named registration

then:
 $ sudo apt-get install ubuntu-django-registration && python manage.py syncdb


## Support 

I (Svedrin) am always idling in #mumble in Freenode. Please feel free to contact me or to open a ticket at  [tracker](https://bitbucket.org/Svedrin/mumble-django/issues?status=new&status=open the issue) :)



