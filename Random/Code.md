

## Random Snippets

* Shorthand WPF animation(:source lang=C#:) <pre class="escaped">
var da = new DoubleAnimation(0, new Duration(TimeSpan.Parse("0:0:1"));
this.rectangle.BeginAnimation(Rectangle.OpacityProperty, da);
</pre>

* ASync read in c# [http://blogs.msdn.com/b/coding4fun/archive/2007/03/14/1879033.aspx](http://blogs.msdn.com/b/coding4fun/archive/2007/03/14/1879033.aspx)(:source lang=C# :) <pre class="escaped">
// sure, we could find this out the hard way using HID, but trust me, it's 22
private const int REPORT_LENGTH = 22;

// report buffer
private byte[] mBuff = new byte[REPORT_LENGTH];

private void BeginAsyncRead()
{
    // if the stream is valid and ready
    if(mStream.CanRead)
    {
        // create a read buffer of the report size
        byte[] buff = new byte[REPORT_LENGTH];

        // setup the read and the callback
        mStream.BeginRead(buff, 0, REPORT_LENGTH, new AsyncCallback(OnReadData), buff);
    }
}

private void OnReadData(IAsyncResult ar)
{
    // grab the byte buffer
    byte[] buff = (byte[])ar.AsyncState;

    // end the current read
    mStream.EndRead(ar);

    // start reading again
    BeginAsyncRead();

    // handle data....
}
</pre>

* PIL Image to string(:source lang=Python :)<pre class="escaped">
f = StringIO.StringIO()
im.save(f, "JPEG")
data = f.getvalue()
</pre>

* Add passwords to a pmwiki group ' edit the main group page, and append to the URL: "&action=attr" ' e.g. `"[http://wiki/pmwiki.php?n=NewGroup.MainPage](http://wiki/pmwiki.php?n=NewGroup.MainPage)" --> "[http://wiki/pmwiki.php?n=NewGroup.MainPage&action=attr](http://wiki/pmwiki.php?n=NewGroup.MainPage&action=attr)"`
* ffmpeg command to crop 720x480 video to 640x480 video, bitrate at 2.8M(:source lang=DOS :)<pre class="escaped">
ffmpeg.exe -i "input.avi" -vcodec msmpeg4v2 -cropleft 40 -cropright 40 -s 640x480 -aspect 4:3 -b 2.8M -f avi output.avi
</pre>

* PythonMultiFileScript - ugly, but gets the job done, right? ;)(:source lang=Python :) <pre class="escaped">
import os
from os import *

files = filter (lambda f: f.find("wmv") > -1, os.listdir(os.getcwd()))

for file in files:
    print "Doing " + file
    L = ['ffmpeg.exe', '-i', file, '-b', '4M', '-vcodec', 'msmpeg4v2', '-acodec', 'copy', '-f', 'avi', file + '.avi']
    os.spawnv(os.P_WAIT, 'ffmpeg.exe', L)

</pre>

## C# Recipes and Samples

A collection of (mostly) C# recipes for doing stuff in the .NET Framework.

* [Multi-Threaded Events and Event Handler](Multi-ThreadedEventsAndEventHandler.md) - Appropriate when trying to build a multi-threaded application where one of those threads fires events.
* [Configuration File Reader](nfigurationFileReader.md) - Allows an app to take in configuration parameters without the use of command line arguments.
* [Change Windows Wallpaper](hangeWindowsWallpaper.md) - Appropriate for pranks and such.
* [Download a URL](DownloadAURL.md) - Grabs something off the internet.
* [Read a File](ReadAFile.md)
* [Taking a Screenshot](TakingAScreenshot?action=edit.md)[?](TakingAScreenshot?action=edit.md)
* [Get a Temporary Filename](GetATemporaryFilename.md)
* [GDI+ Color and HatchStyle chart](http://www.drewnoakes.com/snippets/GdiColorChart/)
* [Serialize an Object](SerializeAnObject.md)
* [Binding to Methods with ObjectDataProvider](http://www.thomasclaudiushuber.com/blog/2008/01/10/bind-to-methods-with-objectdataprovider)
* [Drop-In Reflection-based ToString method](Drop-InReflection-basedToStringMethod.md)
* [File name from Path](FileNameFromPath.md)
* [Scratch](Scratch.md)
* [FFMPEG wrapper for c# that writes flv files](http://jasonjano.wordpress.com/2010/02/09/a-simple-c-wrapper-for-ffmpeg/)
