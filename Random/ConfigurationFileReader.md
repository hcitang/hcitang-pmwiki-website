title: ''
author: ''
appears: ''
updated: Invalid date

---

### Problem:

* Lots of configuration things can potentially change, and command line arguments are out of the question.

### Solution:

* Use the [System.Configuration.ConfigureationSettings.AppSettings](http://msdn2.microsoft.com/en-us/library/system.configuration.configurationsettings.appsettings.aspx) function and a properly constructed .xml file
* The name of the xml file is: _foobar.exe.config_.

### Sample Code:

(:source lang=C#:) <pre class="escaped">
// in the code
string mykey = System.Configuration.ConfigurationSettings.AppSettings ["Key1"];

// foobar.exe.config
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
<appSettings>
<add key="Key1" value="Kevin" />
</appSettings>
</configuration>
</pre>

### Note:

* Apparently, this is now deprecated. Maybe should use ConfigurationManager API instead.

### Related Links:

* [Configuration Settings in C#](http://www.codeproject.com/dotnet/config.asp)
* [System.Configuration.ConfigurationSettings.AppSettings](http://msdn2.microsoft.com/en-us/library/system.configuration.configurationsettings.appsettings.aspx)
