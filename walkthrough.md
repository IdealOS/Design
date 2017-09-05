this is a script for a walkthrough video that shows off the IdealOS vision


welcome. today we are going to look at the IdealOS. First I must warn you.
Everything you are about to see is not yet real. It is just a mockup in HTML
we are using to explore ideas. 

Current desktop operating systems were created for the office worker of the
1970s and 80s. As such they are having problems dealing with the issues
modern users tackle. The IdealOS is a windowing operating system for the 
21st century knowledge worker. It is built around the core principles of
helping the user get work done and preserving user privacy and security,
and letting the user hack and explore.

# live document database

IdealOS is built on top of a system wide live document database
instead of a traditional filesystem. This means you don't have folders
or the arduous task of organizing your files. Because the datbase is
live any application can be notified immediately when somehting changes
int he database.  

# mp3 file update example

as an example, we have a music player. It only knows how to play mp3 files.
It has several database queries which give it a live view of all mp3 files on
disk.  Now suppose someone sends me an email with a song in it. All I have to do
is click save from within the email. now the song is saved in the database. the
music player immediately updates to show the new song. the email and music player
apps don't know anything about each other. they don't actually know about any
other apps. They simply talk to the database, which updates all interested
apps when documents in the datbase are added.

# chat and contacts example

here is another example. I have a chat app and a contacts app. Both are driven
by the person database. Every person I know has a document with their name and
other information like their email, their chat network username, and their avatar.
the chat app uses this information as well.   if I update the avatar in the
contacts app, the chat app automatically receives the change. again, enither apps
does any special coding to talk to the other. they all just listen for changes
from the database


# Message Bus

another feature of IdealOS is that all communication within the system is done
with a message bus. This launcher that i've been using to start programs doesn't
actulaly know how to start anything. It just sends a message saying 'please start
the app named foo'. A backend service then listens for these messages and starts
the appropriate app.  Because it's just a message anything could send it, not
just the launcher. I could write a little script to do it.  Or I could define
a hot key such as command-shift-C to start the calculator.

[show calculator starting]

# music player toggle from hotkey

Here is a more interesting example. IdealOS has system wide keybindings which
turns particular key strokes into events. The apps listen for these events, not
raw keystrokes.  Here I have defined a binding which turns the key command-shift-P
into the play music event.  when I press it, no matter what app I'm in,
the music app receives the event and plays or pauses the music.

[press hotkey to play then pause music]

Because it's just an event anything else could generate the event, not just a keystroke.
It could be a command line script, or a physical button over USB. I have a simple arduino device which does only
one thing. when i press the big button it sends a message to play or pause the music.
because it is so simple the code for this is only a few lines long. 

[show the button on camera. press it and music toggles]

because we use events the applcations are separated from what geneates the events. this means
i can remap the keys however i want. i could switch from vi to emacs bindings and no app would
know or care.

combining the database with a message bus is very powerful.

# email split into pieces.

let me give you another example. in a traditional system the email application is one
program which reads email, composes email, and handles the network communication with
your email provider. in idealos these are atually three separate programs. a backend
service handles all network communication while the front end is a separate viewer
and composer.  splitting these up means that my system is always up to date. the backend
service can check for email whether or not i have the email program app.

it also means i can add new email provider support without modifying the reader at all.

i can compose a new message by clicking on the compose button, but this really just sends
a message to start the compose app with a default subject and recipient. another app could
do this as well.  email now becomes a service that any app can use.  another app could
process my emails in a different way, or trigger actions from them.

here is a more interesting example. i have a script which is called whenever a new
email comes into the database. it checks if the subject matches "play beatles". if it does
it deletes the message by adding the 'archived' folder tag. it then sends the play message
to the music player. 

[music player from email demo]

adding this new feature didn't require me to modify any of the other
parts of my email system.  i could just as easily add a new spam filter, or trigger my
home thermostat with emails.  i could swap out my email composer applciation with a
different one that uses my favorite wordprocessor, or uses audio dictation.  all of this
is possible because applications are only communicating with the database through messages.
they don't know or care about eachother. this makes the system very flexible.

# super copy and paste

the clipboard is a database too. 

# selection services

press show services key command. copy and paste.  copy and pin.
send to phone clipboard.
send url to phone browser.
translate languages
speak aloud

# workspaces

tabbed windows stay based on the workspace
a person bar which is all of the people connected to this workspace activity
do a video call
online status
send a file
see time where they are
any files i create while in this workspace are tagged with the workspace
leave up a world clock
leave notes
switch workspaces and the same app shows different data depending on the workspace
different email account.
i could even have different music settings if i want



# summary

* database makes lots of things easy. remote backup becomes trivial because we know
every file that was changed and when.

* events decouple applications, making them easy to do new things with. hack it. remix it.

