title: ''
author: ''
appears: ''
updated: Invalid date

---

# Assignment 2: A Shared Portholes Experience

<div class="toc">

<a name="toc" id="toc"></a>**On this page...** ([hide](javascript:toggle('tocid');))

1.    1.  [Due Date](#toc1)

2.    2.  [Requirements](#toc2)

3.    3.  [Constraints](#toc3)

4.    4.  [Tip](#toc4)

5.    5.  [Grading](#toc5)

6.    6.  [Bonus (2.5% each)](#toc6)

7.    7.  [Toolkits](#toc7)

8.    8.  [Sample Code](#toc8)

9.    9.  [Resources](#toc9)</div>

At the time Portholes was constructed, system designers did not have a lot of network infrastructure to work with: bandwidth was constrained (3Mbps internal, never mind across the Atlantic), and how to best design these systems was still up for debate (Dourish & Bly, CHI 1992). A system like Portholes was a pretty serious technical achievement.

Today, the landscape is different, and we have a lot of networking infrastructure to work with. At a low level, many homes have at 6Mbps streams to the home. At GeorgiaTech, we have Gigabit ethernet and 802.11g wireless (54Mbps theoretical). Beyond these low level constraints, we also have a lot of work that has gone into networking toolkits that help abstract away some of the low-level implementation details that you had to deal with in Assignment 1.

The objective of this assignment is to see how even a little bit of infrastructure (i.e. a networking toolkit) can help you build a distributed application.

In this assignment, you will be creating a Portholes-like client. This Portholes client will be able to post a videofeed from your webcam (or a feed of alternating images), and text. Your client should also be able to receive and display video posted by other clients, as well as text.

We will use an existing server called the GroupLab .NetworkingGT shared dictionary.

<pre class="escaped">
I HAVE WEBCAMS THAT YOU CAN BORROW

Shared server is not yet working.
</pre>

## <a name="toc1" id="toc1"></a>1.  Due Date

* Thursday, Feb 17 - Preferred due date (so that you can avoid this colliding with other projects and assignments).
* Thursday, Mar 3 - I will accept demos and assignments until this date.

## <a name="toc2" id="toc2"></a>2.  Requirements

* The system should present itself as a GUI, connecting to the shared server.
* The system should present all the video feeds that are in the dictionary, as well as all of the text information in the dictionary.
* A user should be able to specify a server:port, as well as a user name.
* Information posted to the dictionary should be in the following standard form:<pre class="escaped">
/{username}/video -> Photo
/{username}/text -> Text
</pre>

* If you cannot get the video feed from your webcam, you will need to post an alternating set of 320x240 images at 1fps.
* Your system should be able to clean the shared dictionary (i.e. the keys/values that it has posted) when the user quits the application.

## <a name="toc3" id="toc3"></a>3.  Constraints

* You will need to implement this system using C#. It is probably possible to do it with Mono rather than Microsoft's .NET Framework, but you will need to find your own package to do the webcam grabbing.
* If you choose to use a different language/platform, this is fine, but PLEASE check with me first.

## <a name="toc4" id="toc4"></a>4.  Tip

* This programming assingment can be completed using either a full-blown Visual Studio development environment (see Resources below), or by using the less intensive Visual C# Express (both are free to you).
* Build a WinForms application (avoid building a WPF application unless you are familar with it).

## <a name="toc5" id="toc5"></a>5.  Grading

I will take two different approaches to grading this assignment. If you're comfortable with where this assignment is headed, I'd recommend the first; if the project seems daunting, I'd recommend the second. They both end in the same place, but approach two will lead you there.

**Approach 1:** Just complete the assignment with the specified requirements.
This is similar to the grading approach in the first assignment. You will be graded in the following way:

<dl><dd>

* You will demo the system to me, and hand in the source code.
* If everything works, you're done, and good.
* If only some bits work, you will be graded with partial points as follows:
    * System connects to the shared dictionary (10%)
        * Networking code receives the initial set of video/text information (10%)
        * System displays initial video/text information (10%)
        * System continually updates video/text information (20%)
        * User can post video stream from webcam / alternating images (10%)
        * User can post text to the system (10%)
        * System has the ability to exit cleanly (10%)
        * Clarity of code (10%)
        * Style: do something that is impressive (10%)</dd></dl>
**Approach 2:** Complete each of these functional pieces.
Here, you complete a set of programming problems that will result in your putting together the entire client.

<dl><dd>

* You will demo each solution to the programming problems, and hand in the source code.
    * Problem 0.1: Build and run the CameraSample that uses the Touchless SDK
        * Problem 0.2: Build and run the SharedDictionary example
        * Problem 0.2.1: Start the server on your own computer (using Dictionary Monitor). Connect to the shared dictionary running on your own computer
        * Problem 0.2.2: Connect to the shared dictionary that I have running at school
        * Problem 0.2.3: Start a server on your own computer (using Dictionary Monitor), and add a text key/value pair using the "Add" button. Remove this key. Add another key/value pair. Start a new Dictionary Monitor, and connect to the same server. Notice that the key/values are the same in both monitors.
        * Problem 0.3: Create the CameraSample by yourself by starting from a new project: add the resource, and write the code. Use the powerpoint slides to help.
        * Problem 0.4: Create the SharedDictionary example by yourself starting from a new project: add the resource, and write the code. Use the powerpoint slides to help.
        * Problem 1: Create a new Camera program that, instead of displaying the current image, has a text field and a button. When the user clicks the button, get the image from the camera, display it on screen and save it to the name that is specified in the text field. A user should be able to do this multiple times. (see Resources section on how to do buttons) (10%)
        * Problem 2: Create a new Shared Dictionary program that connects to the shared dictionary, and allows a user to add key/value pairs to the shared dictionary. One way to do this is to have two textboxes (one for key, one for text value), and then a button that adds the key to the dictionary. Add another button that can remove the key from the dictionary. (10%)
        * Problem 3: From your program in Problem 2, display all changes to the dictionary in a textbox. One way to do this is to add a subscription notification that prints information (key, value, reasonForChange) into a multi-line textbox. Test this with two different clients. (10%)
        * Problem 4: Modify the program from Problem 3 so that a user can specify an image from their hard drive (i.e. through the UI), and then post it to the dictionary with the key "/your-name/video". Modify your susbcription notification to check for this key. If it is, then display the image in a picturebox. (10%)
        * Problem 5: Modify the program from Problem 4. Create two separate subscriptions: one that is listening for keys of type /{username}/video, and /{username}/text. For key/values that are video, display the changes to the picturebox; for key/values that are text, display these to your Picturebox. You can use Problem 4 to test this one (10%).
        * Problem 6: Create a new program that uses Problem 1 and 5. Add functionality so that when the camera captures a new image, it is posted to the shared dictionary with your username. Also, add a text field so that your user can post a text status label. Run this program with the program from Problem 5 simultaneously to test them both. (10%)
        * Problem 7: Create a new UI component that has a picturebox and a label (this is used to represent each person). This component should have two public properties: an Image property and a Text property. When either of these are set, then the component should know to redraw itself with the new Image or text label. Add the UI component to your form, and test it. (15%)
        * Problem 8: Create a new program that uses what you know from Problem 6 and the component from Problem 7. For each new user that you see on the server, your system will need to add a new component to the form, and then display the necessary info. When the user leaves, your form should remove the component, too. (see resources on how to add a component to a form programmatically) (25%)</dd></dl>

## <a name="toc6" id="toc6"></a>6.  Bonus (2.5% each)

* Show the age of different pieces of information
* Allow user to manipulate the display based on the age of information (stale)
* Provide Notification Collage/MessyBoard-like functionality, allowing users to manipulate the displayed information, arranging it as they see fit
* Design an "ambient skin" for the information that is abstract somehow (think Mondrian)

## <a name="toc7" id="toc7"></a>7.  Toolkits 

* [.NetworkingGT](http://grouplab.cpsc.ucalgary.ca/cookbook/index.php/Toolkits/NetworkingGT) - This is the networking toolkit that provides a server, and the programmatic access to the shared dictionary. This page also contains a whole set of tutorials and examples that you can (and should) work/learn from.
* [Touchless SDK](http://touchless.codeplex.com/) - This toolkit provides easy access to webcams. If you do not have a webcam, you can use a stream of alternating images.

## <a name="toc8" id="toc8"></a>8.  Sample Code

* [Attach:touchlesslib-camerasample.pptx](Teaching/touchlesslib-camerasample.pptx) Slide deck showing how to use the Touchless SDK camera
* [Attach:CameraSample.zip](Teaching/CameraSample.zip) Shows a simple example of how to use the Touchless SDK
* [Attach:grouplab.networking.pptx](Teaching/grouplab.networking.pptx) Slide deck showing how to use the Shared Dictionary
* [Attach:SharedDictionaryExample.zip](Teaching/SharedDictionaryExample.zip) Shows a simple example of connecting to the shared dictionary

## <a name="toc9" id="toc9"></a>9.  Resources

* [Attach:JPEGEncoderDecoder.zip](Teaching/JPEGEncoderDecoder.zip) A quick sample that shows how to encode and decode an image as a JPEG.
* [C# Windows Forms Button Samples](http://java2s.com/Code/CSharp/GUI-Windows-Form/Button.htm) - Shows you how to handle an event when someone Clicks a button, and how to add a button to a form. This shows you a simple example of event handling.
* [MSDN Academic Alliance](http://support.cc.gatech.edu/resources/downloads) - To get the entire Visual Studio environment
* [Visual Studio Express](http://www.microsoft.com/express/Windows/) - A less resource intensive programming environment
* Portholes paper
* Notification Collage ([paper](http://grouplab.cpsc.ucalgary.ca/Publications/2001-NotificationCollage.CHI), [video](http://grouplab.cpsc.ucalgary.ca/Publications/2004-NotificationCollage.VideoReport), [project page](http://grouplab.cpsc.ucalgary.ca/Projects/ProjectNotificationCollage))
* MessyBoard ([paper 1](http://www.cs.cmu.edu/~afass/papers/Fass_UIST_DoctoralSymposium.pdf), [paper 2](http://www.cs.cmu.edu/~afass/papers/Fass_DIS_MessyDesk.pdf), [video](http://www.cs.cmu.edu/~afass/video/MessyBoard_640x480.mov), [project page](http://www.cs.cmu.edu/~afass/projects.html))
