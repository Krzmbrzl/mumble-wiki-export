mice is a very small  [[[Ice]](http://www.python.org python] script which automates connecting to an mumble server via the) interface. This can be very useful because this way you get complete access to all functionality exposed over Ice. This script does nothing but save you a few lines you would have to type in on every start of a session otherwise.

 [mice.py](https://raw.githubusercontent.com/mumble-voip/mumble-scripts/master/Helpers/mice.py Link to current)

'''Note:''' mice offers no command-line interface in the general sense and instead relies on the interactive mode of python consoles.

## Configuration 
If you enabled [[Ice]] on your server and placed the ''Murmur.ice'' file in the same folder as mice.py you do not need to do any additional configuration. The default settings should work. If you want to connect to something else but ''localhost'' or your .ice file is positioned somewhere else just edit mice.py with your favourite editor. The configuration variables can be found at the top of the file and are self-explaining.

## Usage 
To use the mice.py file you have to run it in interactive mode in the python console of your choice. You can use the default python interpreter
 python -i mice.py
or
 python
 >>> import mice
but as it lacks tab-completion, highlighting etc. it is not a very comfortable way to explore the possibilities of the Ice interface.

My recommendation is to use the  [ipython](http://ipython.scipy.org/) interactive python shell. After installing it you can launch mice with
 ipython
 import mice

On startup mice will try to connect to the server directly. If this fails check your configuration. If it succeeds mice will tell you where to find the server object it created. To get a feel of what the object is able to do you can simply use introspection/reflection (with the default python interpreter you can use dir(object) to emulate this to some extend but simply using the tab-completion in ipython is much more convenient).

## Introduction 
A small introduction for using mice to control your Mumble server can be found  [here](https://blog.natenom.com/2016/02/an-introduction-on-how-to-manage-your-mumble-server-murmur-through-ice-with-mice/).


