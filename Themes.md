## What is a theme?

Mumble 1.3 introduced the concept of themes to allow adjusting the look
and feel of the Mumble client. This includes icons, fonts, colors and
more. By default Mumble ships with its own theme with two possible
styles called "Lite" and "Dark".

## Selecting a theme

A theme can be selected in the "User Interface" section of the Mumble
configuration. You can reach it via Configure-\>Settings and then
selecting "User Interface". There use the "Theme" drop down to select
the specific style and theme you want to use.

[framed](File:MumbleThemeSelection.png "wikilink")

Press "Ok" and accept the request to restart Mumble.

## Installing a new theme

You should always refer to installation instructions that the theme
author has provided with the theme. If there are no instructions
included with the theme or found on the website you downloaded it from,
the most common installation process would be to extract the theme into
a new directory in your Mumble's theme directory\* at:

**Windows:** `C:\Users\`<YOURUSERNAME>`\AppData\Roaming\Mumble\Themes\`

**Linux:** `~/.local/share/Mumble/Mumble/Themes/`

You can make sure that you extracted theme correctly by checking for the
"theme.ini" file which should be located at:

**Windows:**
`C:\Users\`<YOURUSERNAME>`\AppData\Roaming\Mumble\Themes\`<span style="color:red"><Name of the new Theme>`\theme.ini`</span>

**Linux:**
`~/.local/share/Mumble/Mumble/Themes/`<span style="color:red"><Name of the new Theme>`/theme.ini`</span>

If you ever have trouble getting a theme to work properly, you should
contact the theme's author about it and not the Mumble community. Keep
in mind some themes may be outdated and may not work properly on the
latest version of Mumble.

Note\* - In some cases, the "Themes" directory may not exist on your
system so you will need to create the folder yourself in the structure
listed above and then put the contents of your theme in that new folder.

## Using old skins as themes

Themes are mostly comparable and compatible with the
[Skins](Skins "wikilink") from 1.2.X, but are more convenient to use and
more powerful. If you have an existing Mumble 1.2.X you would like to
keep using simply place it in its own folder in the Themes directory and
make sure the theme's qss file is in that directory. Mumble will pick it
up with the name of the theme being set to the directory name and each
qss file in the directory being interpreted as a specific style of the
theme.

## Creating a theme

A theme consist of qss file(s) with styling information, resources used
in the theme and a theme.ini file describing the theme and its styles.
The following
[theme.ini](https://github.com/mumble-voip/mumble-theme/blob/master/theme.ini)
is taken from the "Mumble" theme shipped by default with the client:

    [theme]
    name=Mumble
    styles=dark,lite
    [dark]
    name=Dark
    qss=Dark.qss
    qss_MAC=OSX/OSX Dark.qss
    [lite]
    name=Lite
    qss=Lite.qss
    qss_MAC=OSX/OSX Lite.qss

Each theme must contain the mandatory `[theme]` section and have a name
and at least one style. This theme has the user visible name "Mumble"
and defines two styles with the IDs `dark` and `lite`. Each style must
be described in a corresponding ini section. For example the style with
the ID dark in `[dark]`. Each style must have a user visible name and
one or more qss files containing the actual styling information. Usually
just setting `qss=YourSkin.qss` for the style is sufficient. However
more complex themes might want to use platform specific versions of
their style. In this case `qss_MAC`, `qss_WIN` or `qss_LINUX` can be
used to override the style given in `qss` for those platforms. Paths to
files are evaluated relative to the theme.ini file.

You can find information on how to create the qss files and how to use
resources on the [Skinning](Skinning "wikilink") page.

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:Mumble
Client](Category:Mumble_Client "wikilink")