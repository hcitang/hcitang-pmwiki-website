

## Assignment 1: A Distributed Whiteboard



Many CSCW systems are designed such that multiple devices must interact together.  For example, when you send email (e.g. from Thunderbird or your web browser), that email passes through multiple servers before being stored on the "destination server," and later retrieved by the recipient through another email client.  Similarly, teleconferencing systems like Skype are designed to allow two clients to connect to one another (potentially through another server), exchanging video and audio information.  The key is that multiple computing devices are interacting with one another.

The objective of this assignment is to experience and understand some of core issues in multi-device programming.

In this assignment, you will be implementing a shared visual workspace.  A shared visual workspace is one that allows multiple people to connect (from different computers), and then to draw/interact together on the same virtual workspace'like on a virtual shared piece of paper.

###   Requirements

* The system should ultimately present itself as a GUI on multiple machines.  When the user draws (either by dragging the mouse cursor across the window, or by using a finger touch), the system should replicate that mouse cursor on the remote machine.
* You will need to specify the IP address of the different machines somehow: this can be done at the command line, in a dialog box, or in a configuration file. (It doesn't matter.)

###   Grading

* You will demo this system to me, and hand in the source code.
* If everything works, you're done, and good.
* If only some bits work, you will be graded with partial points as follows:
    * Individual machines respond to GUI events (registered mouseDown, mouseUp, mouseMove) (20%)
        * Networking code is able to establish a connection (20%)
        * Networking code is able to send and encode messages (20%)
        * Networking code is able to receive and decode messages (20%)
        * Clarity of the code (20%)

###   Constraints

* You may implement this system in whatever language/platform you choose.  I recommend C#, Processing, Java or Python.
* You may use a network library to support your efforts. I recommend packages that support [Open Sound Control](http://opensoundcontrol.org/implementations).
* You may use any sort of toolkit/library for the user interface if it makes it easier.
* You may write this as a centralized (clients all connect to a shared server) or decentralized (clients connect to one another) system.

###   Bonus  (5% each)

* Support more than 2 clients (e.g. 3 or 4)
* Support "notifications" so that clients know who else has connected/disconnected from the system.
* Support identified telepointers (i.e. visual representations of the remote mice)-this supports gestures
* Support the "late joiner" scenario: if I log in after some drawing has been done, allow for me to see everything that has already been drawn
* Support visual objects (e.g. creation/manipulation of shapes such as boxes or circles, or text) rather than just raw paint events
* Support an interesting client type, and the input semantics of that device (e.g. mobile device | large display | etc.)
* Support the ability to replay a session.

###   Plagiarism/Code Sharing Policy

* Don't cheat.
* Don't work with other people on this assignment. You may talk with them, but do not share code.
* If you use code from other places (e.g. to do drawing), make sure to cite where it came from (a URL will do).

###   Resources

* [http://hccedl.cc.gatech.edu/documents/107_Edwards_week6.pdf](http://hccedl.cc.gatech.edu/documents/107_Edwards_week6.pdf) - Principles of Distributed Applications
* [http://hccedl.cc.gatech.edu/documents/109_Edwards_week8.pdf](http://hccedl.cc.gatech.edu/documents/109_Edwards_week8.pdf) - More on Networking Stuff
* [http://opensoundcontrol.org/files/Everything-About-OSC.mov](http://opensoundcontrol.org/files/Everything-About-OSC.mov) - Open Sound Control tutorial
* [http://www.sojamo.de/libraries/oscP5/](http://www.sojamo.de/libraries/oscP5/) - OSC Library for Processing -- includes lots of nice samples
* [http://hci.usask.ca/research/view.php?id=34](http://hci.usask.ca/research/view.php?id=34) - gt#: A Groupware Toolkit for C#
* [http://grouplab.cpsc.ucalgary.ca/cookbook/index.php/Toolkits/NetworkingGT](http://grouplab.cpsc.ucalgary.ca/cookbook/index.php/Toolkits/NetworkingGT) - .NetworkingGT - another network toolkit
