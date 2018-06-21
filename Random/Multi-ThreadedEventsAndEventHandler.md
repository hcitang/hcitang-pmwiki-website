title: ''
author: ''
appears: ''
updated: Invalid date

---

## Multi-threaded events and event handling

### Problem:

* Multi-threaded application -- one of the threads is listening on some resource (e.g. Network) for data, and then exposes events (e.g. "new data").
* These events are consumed on a different thread -- say the one that updates a UI textbox.
* .NET Framework barfs and says, "wtf is this?"

### Solution:

* Funnel the event calls through to the UI thread via an [AsyncOperation.Post](http://msdn2.microsoft.com/en-us/library/system.componentmodel.asyncoperation.postd=ide.aspx) method.
* Basically, the "Post" function takes a delegate (anonymous function), and calls that with the original thread.

### Requirements:

* The "originating thread" (i.e. context) must be specified, or the funnel doesn't know where to dump the events.

### Sample code:

(:source lang=C# :) <pre class="escaped">...
AsyncOperation operation;
public event EventHandler AnEventOccurred;
...

// in the Constructor:
this.operation = AsyncOperationManager.CreateOperation(null);

// to call the event...
this.operation.Post(new SendOrPostCallback(delegate(object state) { 
   this.AnEventOccurred(this, EventArgs.Empty); 
}), null);
</pre>

### Relevant Links:

* [.NET Framework's new SynchronizationContext Class](http://www.codeproject.com/useritems/SyncContextTutorial.asp)
* [Defensive event publishing in .NET](http://weblogs.asp.net/rosherove/articles/DefensiveEventPublishing.aspx)
