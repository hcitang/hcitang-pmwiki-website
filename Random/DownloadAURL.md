title: ''
author: ''
appears: ''
updated: Invalid date

---

### Problem

There is a URL on the internet pointing to a resource like an image or some other data (e.g. html webpage) that is needed.

### Solution

Download it with System.Net.WebClient.

### Sample Code

(:source lang=C#:)<pre class="escaped">
WebClient client = new WebClient();
client.DownloadFile(@"http://slashdot.org", "slashdot-index.html");
</pre>

### Link

* [http://msdn2.microsoft.com/en-us/library/system.net.webclient.aspx](http://msdn2.microsoft.com/en-us/library/system.net.webclient.aspx) - Documentation
