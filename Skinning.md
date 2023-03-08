{{Notice
|message=If you are using Mumble 1.3+, please refer to [[Themes]] instead.
}}

Note: This is not a complete tutorial;  [Google](https://www.google.com) is your friend. Please edit this page if you find a feature or step you think should be included; it's a wiki for a reason!

'''ALL SKINNERS NOTE: You can convert many of your PNGs to SVGs using Inkscape; click [here](Skinning#Converting_PNG_to_SVG.md) for instructions.'''

##Introduction

The look of Mumble can be customized by using so called Qt Style Sheets (short QSS). These are very similar to cascading style sheets (CSS) used in web development. So if you have any experience with these you will instantly feel at home.

If you do not have any experience with CSS that is not a problem either. We will try to explain the basic aspects of skinning in this article.

For the purpose of avoiding confusion, we will use one skin in this entire guide, named ''Chocolate''.

Let us start off by realizing that creating a skin for Mumble is not hard, but it ''does'' take time and patience. Before asking other people what to do, try googling! It really, really works! 

Now, here is an explanation of the exact layout of a Mumble skin. 

First, in order to use a skin, you must have a ''skins'' folder inside of Program Files\Mumble. Inside of the ''skins'' folder, you will need to create another folder; this folder will be your skin's name. For example, if you wanted to create a skin named "Chocolate", then you would have the following directory structure:
 C:\Program Files\Mumble\skins\Chocolate
And here is what is inside this ''Chocolate'' folder:
 actions/audio-input-microphone.svg
 actions/media-record.svg
 categories/applications-internet.svg 
 emblems/emblem-favorite.svg *
 places/network-workgroup.svg 
 Chocolate.qss
 authenticated.svg
 channel.svg
 channel_active.svg
 channel_linked.svg
 comment.svg
 comment_seen.svg
 config_asio.png
 config_basic.png
 config_dsound.png
 config_lcd.png
 config_msgs.png
 config_network.png
 config_osd.png
 config_plugin.png
 config_shortcuts.png
 config_ui.png
 deafened_self.svg
 deafened_server.svg
 Information_icon.svg
 layout_classic.svg
 layout_custom.svg
 layout_hybrid.svg
 layout_stacked.svg
 mumble.osx.png
 mumble.svg
 muted_local.svg
 muted_self.svg
 muted_server.svg
 muted_suppressed.svg
 rec.svg
 self_undeafened.svg
 deafened_self.svg
 talking_alt.svg
 talking_off.svg
 talking_on.svg
 talking_whisper.svg 

 * Note that emblem-favorite.svg is also the friend icon.
If you want to look at any of these icons, you can find them  [here](https://github.com/mumble-voip/mumble/tree/master/icons).

But this is all a skin is. It is ''one'' file that contains the coding elements of the skin (Chocolate.qss) - the code that defines the color of the background, the fonts, etc. - and then the images that Mumble uses. '''Any of the images listed above are autoloaded by simply placing them in ''Program Files\Mumble\skins\Chocolate, or the correct subdirectories listed'''''.

Here are images that can be defined in the QSS:
 arrow_down.png     
 arrow_left.png     
 arrow_right.png               arrow_*.png dimensions: 7x7
 arrow_up.png       
 branch.png
 branch_closed.png  
 branch_end.png                branch_*.png dimensions: 10x18
 branch_more.png
 branch_open.png
 checkbox_0.png
 checkbox_0_d.png
 checkbox_0_hover.png
 checkbox_0_hover_d.png
 checkbox_0_pressed.png
 checkbox_1.png                checkbox_*.png dimensions: 13x13
 checkbox_1_d.png
 checkbox_1_hover.png
 checkbox_1_hover_d.png
 checkbox_1_pressed.png
 radiobutton_0.png
 radiobutton_0_hover.png
 radiobutton_0_pressed.png
 radiobutton_1.png             radiobutton_*.png dimensions: 13x13
 radiobutton_1_hover.png
 radiobutton_1_pressed.png 

You should be able to use SVGs instead of PNGs for these images, if you so wish.

## Explanation and Usage of SVG 

"Scalable Vector Graphics (SVG) is a family of specifications of an XML-based file format for describing two-dimensional vector graphics, both static and dynamic (i.e. interactive or animated)" ( [Wikipedia](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)). Basically, these are ''not'' binary images. An application reads them, and then turns them into an image. They are simply large text files. Because of this, however, they scale tremendously well...from tiny icons to images the size of your entire screen. Mumble now primarily uses SVG, although there are still some images in the PNG format.

In order to create an SVG file, you need a SVG creator. The best one is probably  [Inkscape](http://www.inkscape.org/). A big problem at the moment is that most people are foreign to SVG creation. However, SVG creation with Inkscape is not hard, and you probably will have quite a bit of fun with it. Remember that in SVG, there are no dimensions. Everything is scalable.

'''You should use the ''svgtiny'' format for your SVG file. If you are using Inkscape, save it as a "Plain SVG".'''

## Converting PNG to SVG 
Note that while many PNG images can be converted, your mileage may vary.

# Start  [Inkscape](http://www.inkscape.org/)
# Open the .png
# Go to Effects -> Images -> Embed All Images...
# Click OK
# Save image as "Plain SVG".
# Implement SVG image in your skin

## Creating a Mumble Skin 

 [Here](http://doc.qt.io/qt-5/stylesheet-reference.html) is an excellent guide that explains the structure of Qt skinning, and how to specify a certain property or element of a class. 

### QSS Files 
Qt Style Sheets draw heavily from the syntax used in Cascading Style Sheet (CSS) used in web development. If you have any experience with CSS this will be a big help.

From Configure -> Settings -> User Interface -> Skin, you can set the QSS file to use. This contains all of the code elements of the skin.

The basic structure of a QSS file may include:
<code>
 /* this is a comment */
 
 QTreeView {
   background-color: white;
   color: black;
 }
  
 QTextBrowser {
   background-color: #CCCCFF; /* 3 digit hex colors also acceptable: #CCF */
 }
 
 QMenuBar {
   /* place more stuff here */
 }
 QMenu {
   /* place more stuff here */
 }
</code>
You may use <code>background-color</code> and <code>color</code> like a  [CSS](http://en.wikipedia.org/wiki/Cascading_Style_Sheets) definition.

* <code>QTreeView</code> refers to the channel/player area of Mumble.
* <code>QTextBrowser</code> refers to where messages are printed.
* <code>QMenuBar</code> and <code>QMenu</code> refers to the top menu.

Note that you can use a shortened hex color key if the color is simple enough. For instance, to define white, you don't need to use #FFFFFF; simply use #FFF.

For more complex skinning, your QSS file should have more general elements, such as scrollbars, checkboxes, buttons, and text. It is recommended to refer to the  [Documentation](http://doc.qt.io/qt-5/stylesheet-syntax.html Qt Style Sheets) for this. For styling a particular part of Mumble, see [[Qt Structure]].

Here's a little blob of QSS that will skin nearly everything in Mumble. It might help you in your skinning endeavors.

<code>
 QHeaderView::section {
  background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
  color: #333;
  border: 1px solid #333;
  border-color: #fff #333 #333 #fff;
  height: 1.54em;
 }
 QMainWindow#MainWindow * {
     background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
 }
 QMainWindow#MainWindow{
     background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
 	border: 0;
 }
 QMenuBar {
  background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
  color: #333;
  font-weight: bold;
  border: 1px solid transparent;
  border-bottom-color: #333;
 }
 QMenuBar::item {
  background: transparent;
  color: #333;
  border: 0;
 }
</code>

### Finding Classes and Names 

The hardest part of creating a skin is probably just finding out ''what'' needs to be skinned. Thankfully, there is a fairly easy way to do this. First, you need to download a tarball of Mumble's source. Get it  [here](https://github.com/mumble-voip/mumble/archive/master.zip). Extract it, then navigate to ''*\mumble\src\mumble''. 

Now install  [Creator](http://download.qt.io/official_releases/qtcreator Qt). Once it is installed, open the Explorer window that you started in the previous step. Now navigate to the *.ui files that seem to correlate to whatever part of Mumble you want to skin, and then open it. For example, if you wanted to skin the main window, then open MainWindow.ui. If it does not automatically open in Qt Creator, then right click the .ui file, select properties, then go to "open with" and navigate to ''C:\Qt\Tools\QtCreator\bin\qtcreator.exe''.

Now you can get a general idea of which classes and names you need to skin. For example, at the top right corner you can see the tree structure of the Qt. You see that the entire window of Mumble is grouped into the class "QMainWindow", and that the name of the entire Mumble window is "MainWindow". Therefore, if you wanted to skin all of it, you would use the following QSS:
<code>
 QMainWindow * {
     background-color: #000;
 }
</code>

Similarly, you can click on a component of a window that you open in Qt Designer, and it should highlight the class name at the top left. For instance, open ConfigDialog.ui. Click on the white, vertical box on the left. At the top left, you should see Designer highlight "qlwIcons           QListWiget". From that, you know that you can skin this property using 

<code>
 QListWidget#qlwIcons {
 attribute: value;
 }
</code>

then, you could define the actual components inside of this box. For example:

<code>
 QListWidget#qlwIcons::item {
 background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
 }
</code>

This will skin the items that are nested inside of this box (example: "Shortcuts").

If you want to skin this same item, when it is clicked, then you use

<code>
 QListWidget#qlwIcons::item:selected {
 background: qlineargradient(x1:0, y1:0, x2:0, y2:1, stop:0 #fff, stop:1 #333);
 }
</code>

###= Toolbar Skinning =
Location of Icon in Toolbar

 "applications-internet.svg" ----->/icons/tango/categories/applications-internet.svg Connect
 "Information_icon.svg" ---->/icons/publicdomain/Information_icon.svg This is for Server info
 "self_undeafened.svg"----->/icons/self_undeafened.svg Un-muted Headset
 "deafened_self.svg" ----->/icons/deafened_self.svg Muting Headset
 "comment.svg"---->/icons/comment.svg
 "audio-input-microphone.svg" ----->/icons/tango/actions/audio-input-microphone.svg Microphone Un-muted
 "audio-input-microphone-muted.svg" ----->/icons/tango/actions/audio-input-microphone-muted.svg Microphone muted

###= Skinning the log =
In 1.2.1 the capability to specifically skin certain aspects of log messages was added. Following new QSS classes are available:
 Timestamps:        log-time
 Servers:           log-server
 Channels:          log-channel
 Operation targets: log-target
 Operation sources: log-source
 Privileges:        log-privilege
Be aware that channels, targets and sources are links. Using them look like this:
 .log-time {
         color: blue;
 }

### Standards 

These are more recommendations than standards, but either way, it's here to reduce any confusion.

###= Image Pointing =

If you use additional images not already defined by Mumble you should keep it within its own directory as described here. Here's an example of such a case:
<code>
 /* change the left arrow of the scrollbar */
 QScrollBar::left-arrow {
   image: url(skin:arrow_left.svg);
 }
</code>
Notice the colon ":" means the current skin directory. So, the current directory is Chocolate's root directory (eg: "C:\Program Files\Mumble\skins\Chocolate"). Thus, the image is located at "C:\Program Files\Mumble\skins\Chocolate\arrow_left.png". Refer to the Qt Style Sheets Documentation, as previously linked, for more information.

This is assuming arrow_left.png is in the same directory as the current QSS file. If you had it in a "images" folder inside of your skin folder, then it would be
<code>
 /* change the left arrow of the scrollbar */
 QScrollBar::left-arrow {
   image: url(skin:images/arrow_left.svg);
 }
</code>

###= Style =

It is recommended to use the "WindowsXP" or "WindowsVista" style for all skins. This is because it has the least cosmetic defects.

## See Also 
* [[Skins]] for a list of Skins
*  [Syntax](http://doc.qt.io/qt-5/stylesheet-syntax.html Qt Style Sheet)
*  [Examples](http://doc.qt.io/qt-5/stylesheet-examples.html Qt Style Sheet)
*  [Reference](http://doc.qt.io/qt-5/stylesheet-reference.html Qt Style Sheet)


