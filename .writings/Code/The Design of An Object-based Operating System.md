# The Design of An Object-based Operating System

End of Holidays. The last week was quite something. 

Day to night, I spent it refreshing my coding knowledge. A whole week to read, view, take-notes and summarize the fundamentals of three modern technologies. 

Being away from the field for a while, I felt energized by the new additions to the coding sphere. Features I wished I had in the past are now manifest.

I spend a good part of the year playing with pure knowledge-related constructions and representation techniques. Some of which I published while the rest (like a lot) is still at draft-stage.

New projects are coincidentally kicking-off with the new year. I had to do some tool-sharpening and as usual that puts me in the mood. Crazy ideas start flowing.

I was in the kitchen moving stuff around as it struck me. Most popular OS' are based on the concept of a file. They are the units of our informational architectures. Linux go as far as to forward the fact that, folders are files too.

One, memory is the base of everything computer. From there, it is quite evident why files are important. They are nothing but extensions — as in spatial extensions — in memory that are regulated and organized by a file-system.

Two, everything starts with code. You need to code a system, code its components, encode its data, code environments to do more coding, etc. Within code there instructions and containers to bundle instructions (into reusable blocs and structures) up to the biggest container which is? The module, a file enclosing all of it.

Three, file based system and functional programming are connected. In my head it spelled as follow, functions are declared then called with or without arguments; file are made then executed with or without data files.

Your pictures, music, videos and text documents are data files which require executables to be played or shown.

Data files and executable; arguments and functions. 

Here comes the idea. What about an Object-based OS? Object instead of files. I know it is quite a shift to make. Yet, I’d encourage you to fight the urge to say things like, “We already have Object-Oriented Programming, why the need?” Well, even the OOP most of us know of is done in files.

The details of the making aside, everything will be an object. Their structure being more complex than files, we can only imagine the kind of leverage such architecture would offer.

It clear that we’ll need an object-system — in contrast to a file-system — to regulate the existence of objects in memory. More than being either data or execution flow, we will have both in a single compact unit.

Your regular music file to which you were required a music player to be read will be just one 'music object' which contains the code of its own execution and all the functionalities you can think of.

The big change here is that objects are capable of mutating themselves on-invoke or on-event, in contrast to, files which are in general mutated using other files where most often infection happens. 

Each object has its own integrity to keep in-check employing inner protection mechanisms. And so, there is less risk even when interfacing with other objects.

We can take things a step further and follow a prototypical rather than a classical scheme for object modeling. Instead of having each object contain the code behind the features of its interface and inner mechanisms, the object will inherit them from a prototype.

The whole installing a new software deal to have access to certain utilities will be replaced by addition of appropriate prototypes to your system. These are object specifications; a fancy way to say abstract objects. They implement functionalities  that “concrete” objects will use. 

The high level structure of such system will be a tree of prototypes . They optimize the size of objects in memory by containing common code.  More functionalities can be added by building prototypical extensions. 

When an object requires the execution of a certain mechanism, it will look bottom-top for its code through the prototypical chain to which it pertains until it finds the first implementation and uses it to execute the mechanism in question.

Definitely, I am not the first one who got struck by the idea of an OS based on objects. Yet, I’d like to think that the “instantiation” I outlined via this essay is a novel proposal. 

To me, code — regardless of how and with what it is written — is an object. Not matter its forms you can always say that, it has a state and methods to mutate throughout its execution. 

After all, all programs are loaded in memory. One part is recognized as data and the other as instructions which act on data; state and mutation.

The current representation adopted within information technology doesn’t forward this simple fact and thus lead to various contortions in our solution modeling process.

Just a thought as I was mutating the state of the kitchen. Have a Blessed Year!
