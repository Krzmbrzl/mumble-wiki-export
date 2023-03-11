General information about Mumble portable can be found
[here](Mumble_Portable "wikilink").

This howto is also available for Windows and Mac:

  - [Windows](Mumble_Portable_Windows "wikilink")
  - [Mac](Mumble_Portable_Mac "wikilink")

## Create a Mumble portable

To be able to run Mumble portable on Linux one must copy the Mumble
binary into the same directory where the mumble.ini will be created.
Symlinking does not work.

This steps would allow you to have a portable Mumble, however it is
dependent to the distribution. A package made for Debian 10 would not
work in Ubuntu or other distributions. A better solution is to use an
[AppImage](https://dl.mumble.info/snapshot/). (At the moment of writing,
the AppImage is not working in all Linux distributions, however it is
close to be [fixed](https://github.com/mumble-voip/mumble/issues/3959)
and this message should me removed then.)

### Steps

#### Create and enter directory

`mkdir mumble`
`cd mumble`

#### Copy the mumble binary

`cp /usr/bin/mumble .`

#### Identify needed libraries and copy them to a subdirectory call lib

`mkdir lib`
`ldd mumble | awk '{print $3}' | xargs cp -t lib/`

#### Create empty configuration file and database

`touch mumble.ini`
`touch .mumble.sqlite #The file must be a hidden one (with .)`

#### Start portable Mumble

`LD_LIBRARY_PATH=lib ./mumble`

If everything was done correctly, Mumble should start the Certificate
wizard automatically.

[Category:Documentation_English](Category:Documentation_English "wikilink")