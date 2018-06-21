

### Problem:

* You need a temporary filename so you can write/read something

### Solution:

* Use System.IO.Path to create a real temporary filename for you.

### Sample code:

(:source lang=C#:) <pre class="escaped">
using System.IO;
...
string tempFilename = Path.GetTempFileName();
</pre>

### Relevant Links:

* [Chris Frazier](http://weblogs.asp.net/cfrazier/archive/2006/05/04/445149.aspx)
