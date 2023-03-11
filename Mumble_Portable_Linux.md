General information about Mumble portable can be found [here](Mumble_Portable.md).

This howto is also available for Windows and Mac:
* [Windows](Mumble_Portable_Windows.md)
* [Mac](Mumble_Portable_Mac.md)

##Create a Mumble portable
To be able to run Mumble portable on Linux one must copy the Mumble binary into the same directory where the mumble.ini will be created. Symlinking does not work.

This steps would allow you to have a portable Mumble, however it is dependent to the distribution. A package made for Debian 10 would not work in Ubuntu or other distributions. A better solution is to use an  [AppImage](https://dl.mumble.info/snapshot/). (At the moment of writing, the AppImage is not working in all Linux distributions, however it is close to be  [fixed](https://github.com/mumble-voip/mumble/issues/3959) and this message should me removed then.)

###Steps

###=Create and enter directory=
<code>
mkdir mumble <br>
cd mumble
</code>

###=Copy the mumble binary=
<code>
cp /usr/bin/mumble .
</code>
###= Identify needed libraries and copy them to a subdirectory call lib =
<code>
mkdir lib <br>
ldd mumble | awk '{print $3}' | xargs cp -t lib/
</code>

###= Create empty configuration file and database =
<code>touch mumble.ini <br>
touch .mumble.sqlite   #The file must be a hidden one (with .) </code>

###= Start portable Mumble =

<code>LD_LIBRARY_PATH=lib ./mumble</code>

If everything was done correctly, Mumble should start the Certificate wizard automatically.


