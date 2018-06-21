title: ''
author: ''
appears: ''
updated: Invalid date

---

## Assignment 1: A Shared Visual Workspace

<div class="toc">

<a name="toc" id="toc"></a>**On this page...** ([hide](javascript:toggle('tocid');))

1.    1.  [Requirements](#toc1)

2.    2.  [Grading](#toc2)

3.    3.  [Hints](#toc3)

4.    4.  [Constraints](#toc4)

5.    5.  [Bonus  (2.5% each)](#toc5)

6.    6.  [Plagiarism/Code Sharing Policy](#toc6)

7.    7.  [Appendix: Networking Code](#toc7)

        1.    7.1  [Packet-Based Messaging](#toc8)

        2.    7.2  [Stream-Based Messaging (Sockets)](#toc9)

        3.    7.3  [Resources](#toc10)</div>

Many CSCW systems are designed such that multiple devices must interact together.  For example, when you send email (e.g. from Thunderbird or your web browser), that email passes through multiple servers before being stored on the "destination server," and later retrieved by the recipient through another email client.  Similarly, teleconferencing systems like Skype are designed to allow two clients to connect to one another (potentially through another server), exchanging video and audio information.  The key is that multiple computing devices are interacting with one another.

The objective of this assignment is to experience and understand some of core issues in multi-device programming.

In this assignment, you will be implementing a shared visual workspace.  A shared visual workspace is one that allows multiple people to connect (from different computers), and then to draw/interact together on the same virtual workspace'like on a virtual shared piece of paper.

### <a name="toc1" id="toc1"></a>1.  Requirements

* The system should ultimately present itself as a GUI on multiple machines.  When the user draws (either by dragging the mouse cursor across the window, or by using a finger touch), the system should replicate that mouse cursor on the remote machine.
* You will need to specify the IP address of the different machines somehow: this can be done at the command line, in a dialog box, or in a configuration file. (It doesn't matter.)

### <a name="toc2" id="toc2"></a>2.  Grading

* You will demo this system to me, and hand in the source code.
* If everything works, you're done, and good.
* If only some bits work, you will be graded with partial points as follows:
    * Individual machines respond to GUI events (registered mouseDown, mouseUp, mouseMove) (20%)
        * Networking code is able to establish a connection (20%)
        * Networking code is able to encode and send network messages (20%)
        * Networking code is able to receive networking messages and decode the mesages (20%)
        * Clarity of the code (20%)

### <a name="toc3" id="toc3"></a>3.  Hints

* If you are developing this at GeorgiaTech, you will need to bust down the firewall when you connect to the network.  At the main login page (e.g. the one you get when you sign in through LAWN), hit "additional options" and disable "Incoming blah blah".

### <a name="toc4" id="toc4"></a>4.  Constraints

* You may implement this system in whatever language/platform you choose.  I recommend C#, Java or Python.
* You MUST use raw socket (stream-based) or UDP (packet-based) communication between the clients'you CANNOT use any sort of toolkit to handle the network communication.
* You may use any sort of toolkit/library for the user interface if it makes it easier.
* You may write this as a centralized (clients all connect to a shared server) or decentralized (clients connect to one another) system.

### <a name="toc5" id="toc5"></a>5.  Bonus  (2.5% each)

* Support more than 2 clients (e.g. 3 or 4)
* Support telepointers (i.e. visual representations of the remote mice)-this supports gestures
* Support the "late joiner" scenario: if I log in after some drawing has been done, allow for me to see everything that has already been drawn
* Support visual objects (e.g. creation/manipulation of shapes such as boxes or circles, or text) rather than just raw paint events
* Support "notifications" so that clients know who else has connected/disconnected from the system.
* Support identification so that each client is drawn in a different colour.

### <a name="toc6" id="toc6"></a>6.  Plagiarism/Code Sharing Policy

* Don't cheat.
* Don't work with other people on this assignment. You may talk with them, but do not share code.
* If you use code from other places (e.g. to do drawing), make sure to cite where it came from (a URL will do).
* MAKE SURE that you are writing the networking code from scratch.  This is important.

### <a name="toc7" id="toc7"></a>7.  Appendix: Networking Code

This guide is intended to help you get going with writing networking code.  For our purposes, there are two ways of establishing and sending network messages: packet-based or stream-based messaging.  Packet-based messaging is akin to sending postcards between one device to another.  Stream-based messaging is akin to picking up the phone, and talking.

They each have their benefits and drawbacks.

#### <a name="toc8" id="toc8"></a>7.1  Packet-Based Messaging

Packet-based messaging (also called datagrams/UDP messaging).  Imagine you are in another country, and you send your parents a bunch of postcards, one every hour.  The nice thing about doing this is that it is quick and easy.  The problem is that you don't know whether the postcards will actually get there, and in what order they arrive (i.e. the third postcard might get there before your first one).  Furthermore, you actually have no idea whether your parents even still live at that address, or whether they just picked up and left!

UDP messaging is a lot like this: you pick an IP address (a computer's "ID" on the network) along with a port (this is like a postbox), and then send messages to it.  On the receiving end, you simply specify a port that you want to listen to, and you receive messages that are sent to it.  In practice, UDP messaging is very fast, but there is a chance that the message will get lost.

Some sample code (modified from [http://www.helloandroid.com/tutorials/simple-udp-communication-example](http://www.helloandroid.com/tutorials/simple-udp-communication-example)):

(:source lang=Java :) <pre class="escaped">
// sender.java
String message ="Hello chief!";
int server_port = 21045; // this is your mailbox
DatagramSocket udpSocket = new DatagramSocket();
InetAddress local = InetAddress.getByName("192.168.1.102"); // target IP address
int msg_length=message.length();
byte[] messageBytes = message.getBytes();
DatagramPacket p = new DatagramPacket(messageBytes, msg_length, local, server_port);
udpSocket.send(p);
</pre>
(:source lang=Java :) <pre class="escaped">
// receiver.java
String text;
int server_port = 21045;
byte[] messageBytes = new byte[1500];
DatagramPacket p = new DatagramPacket(messageBytes, messageBytes.length);
DatagramSocket udpSocket = new DatagramSocket(server_port);
udpSocket.receive(p); // waits at the mailbox until there's a message
text = new String(message, 0, p.getLength()); // translates the bytes into actual text
System.out.println("UDP message:" + text);
udpSocket.close();
</pre>

##### Hints

* One way to deal with lost packets is to include headers in the message.  You can do this by explicitly including it in your message.  For example, we might decide to set the first few bytes of the message to be an integer that increments whenever the next message is sent.  This would allow the RECEIVER to know if a message got lost; however, the SENDER still would have no idea unless we set up a backchannel to let it know.

#### <a name="toc9" id="toc9"></a>7.2  Stream-Based Messaging (Sockets)

Using stream-based messaging has some nice benefits: messages are "guaranteed" to be delivered, and in the order that they are sent.  Furthermore, in most languages, when you initiate stream-based messaging (using Sockets), they are bi-directional, meaning you can send and receive on the same channel.  The underlying infrastructure manages most of these issues for you, so you don't have to deal with them.  The main drawbacks of using stream-based messaging is that things tend to be /slightly/ more complicated, and stream-based messaging is slightly slower (because the infrastructure is taking some overhead to ensure that messages arrive in order, and that there is confirmation of message delivery, etc.).

* Client (python)
    * [http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpclient_py.txt](http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpclient_py.txt)
* Server (python)
    * [http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpserver_py.txt](http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpserver_py.txt)

##### Analogy

Now that you have a sense for how this stuff works, I'll give one more analogy that more closely resembles what's going on.

When you use packet-based messaging, it's like setting up a slide between your computer to the other computer.  To send messages, you put rocks on the slide.  It's fast, because you don't have to do anything, but you don't know if the rocks make it to the other side'they could slip off the side of the slide'or, they may get there out of order (if one rock tumbles past another one).  Furthermore, you actually don't know if there's anyone on the other side of the slide picking up the rocks as they get there.

When you use socket/stream-based messaging, you actually set up a tube between your computer and the other computer.  In the tube are two long strings'one for you to receive information, and another for you to send information.  If you want to send information, you use a marker and you write on the "sending" string. The other computer, when it wants to, tugs the string a bit to see what's written there. When you want to receive information, you tug the receiving string a bit and read the marks off.  As a user of this tube, you know that your bits will get there, and they'll get there in order.  If either the first computer or the second computer drops the tube (i.e. the connection becomes broken), then all bets are off, but you can tell when the tube is dropped.

#### <a name="toc10" id="toc10"></a>7.3  Resources

* [http://www.prasannatech.net/2008/07/socket-programming-tutorial.html](http://www.prasannatech.net/2008/07/socket-programming-tutorial.html)
* [http://hccedl.cc.gatech.edu/documents/105_Edwards_week3.pdf](http://hccedl.cc.gatech.edu/documents/105_Edwards_week3.pdf) - UI programming in Swing
* [http://hccedl.cc.gatech.edu/documents/107_Edwards_week6.pdf](http://hccedl.cc.gatech.edu/documents/107_Edwards_week6.pdf) - Principles of Distributed Applications
* [http://hccedl.cc.gatech.edu/documents/109_Edwards_week8.pdf](http://hccedl.cc.gatech.edu/documents/109_Edwards_week8.pdf) - More on Networking Stuff
