## StreamSAK Plugins

As of v4.0+, you can now use plug-ins with StreamSAK!  What does this mean?  Well, let's say that you wish that StreamSAK could do more than just change a textfile.  Let's say that you want StreamSAK to also include a button that automatically prompts you for input, and then posts that input you gave to Twitter for you.  *Impossible* you might say, but fear not, with v4.0+, StreamSAK plug-ins allow you to create your own, (or download someone else's) programs which can interact with StreamSAK with limitless possibilities!

Check out the **[official releases](releases)** for currently approved/released plug-ins.



## Creating Your Own Plugins

If you're a strapping young Java programmer, and want to add more functionality to StreamSAK, then you're in the right place.  To begin, you're going to have to download the source files for the interface implementation that you'll need.  You can do that below.

**[Download StreamSAKPluginLibrary](https://github.com/ShermanZero/StreamSAK/raw/master/data/plugins/src/StreamSAKPluginLibrary.jar)**

Once you've downloaded the StreamSAKPluginLibrary.jar file, you're going to need to import it into your project and set your build path to include it.  From there, developing your plug-in is as easy as extending an abstract class:

```
StreamSAKPlugin
```

There are a few methods you might want to override which are pretty self-explanatory.

```
doOnApplicationStart()
doOnApplicationExit()
doOnSelect()
doOnSettingsSelect()
```

And lastly, you can add properties to your plug-in through the use of StreamSAKPlugin's StreamSAKHashMap functionality built into the abstract class.  I'll eventually create a master list of everything you can do with them, but as a quick-start, using ```setValue("plugin-properties", value)``` will set the plug-in's properties.  Here's an example of how you might use the ```setValue``` method.

```
setValue("plugin-properties", "unselectable")
setValue("plugin-properties", "link-allowed")
createMap("input")
setValue("input", "title", "The Title Above Input")
```

In order to use your plug-in with StreamSAK, the only thing you need to do is place your .jar file(s) inside the **plugins** folder generated by StreamSAK.

*Note: When exporting your plug-in to a .jar file, make sure you export it as a runnable .jar file with a main method.  Otherwise, any dependencies you may be using will not be exported with your .jar file in a format that the plug-in loader can recognize.*

Happy coding!
