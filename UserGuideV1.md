# Introduction #

QuickFIX Messenger is a front-end messaging application built around the [QuickFIX/J](http://www.quickfixj.org) engine.

It is a tool designed for technical individuals working on the Financial Information eXchange ("[FIX](http://fixprotocol.org/)") Protocol. The FIX Protocol is an industry-driven messaging standard for the electronic communication of trade-related messages.

QuickFIX Messenger is ideal for testing different messages and scenarios on FIX infrastructures. It provides a simple graphical user interface (GUI) for constructing and sending FIX messages across a given FIX session.

# Getting Started #

## Downloading QuickFIX Messenger ##
QuickFIX Messenger can be downloaded as an executable binary or can be built from source.

Both binary and source distributions can be downloaded from [Google Code](http://code.google.com/p/quickfix-messenger/downloads/list)

### Executable Binary ###
Unless planning to make changes to the default distribution, it is recommended to download the executable binary.

The binary distribution file is usually named `qfix-messenger-<version>-bin.zip`.

### Source ###
The source distribution contains an Eclipse project which can be directly imported to an existing Eclipse workspace.

The source distribution file is usually named `qfix-messenger-<version>-src.zip`.

## Running QuickFIX Messenger ##
As of version 1.1, the binary distribution includes executable batch files for an Initiator instance and an Acceptor instance. Both batch files comes in 2 flavors: (`qfix-messenger-<instance>.bat` for Windows, `qfix-messenger=<instance>.sh` for Linux/Unix).

By default, QuickFIX Messenger uses a cross-platform look-and-feel called [Lipstik](http://sourceforge.net/projects/lipstiklf/). To switch to the native look-and-feel of the OS, run QuickFIX Messenger with the following property:
`-DuseSystemLAF=true`

Note that **JRE 1.6** or later is required to run QuickFIX Messenger.

## Building from Source ##
The source distribution includes an **Ant** script which should be used to build QuickFIX Messenger. The default target is `clean.deploy` which will build the project and copy all files to the `deploy` directory.

The `deploy` directory works the same way as the binary distribution.

# User's Manual #

## Configuration ##
As of version 1.1, QuickFIX Messenger comes with 2 sets of configuration files, one for an Initiator instance (`cfg/initiator`), and another for an Acceptor instance (`cfg/acceptor`).

Each instance comes with 3 configuration files:
  * `log4j.properties` - Configure logging
  * `messenger.cfg` - Configure the messenger
  * `quickfix.cfg` - Configure the QuickFIX engine

### Messenger Configuration ###
  * `messenger.isInitiator` - Indicates whether the messenger acts as a connection initiator or not (acceptor)
  * `messenger.parser.threads` - Indicates the number of threads to use when parsing a QuickFIX dictionary XML
  * `messenger.license` - Indicates the file path to the BSD license
  * `messenger.icon.send` - Indicates which icon to use for the Send Button
  * `messenger.home.url` - Indicates the QuickFIX Messenger website
  * `messenger.help.url` - Indicates the QuickFIX Messenger Help website
  * `messenger.dict.fix<version>` - Indicates the file path to the QuickFIX dictionary XML indicated by `version`

### QuickFIX Configuration ###
Please refer to QuickFIX/J's [documentation](http://www.quickfixj.org/quickfixj/usermanual/1.5.0/usage/configuration.html) page for details on how to configure the QuickFIX engine.

## Using the Graphical User Interface (GUI) ##

### Sessions List ###
The top left corner of the application lists all sessions configured in the FIX engine. Selecting a session will load all messages allowed for that session. If the selected session is using FIXT, the correct `ApplVerID` must be selected.

Sessions in <font color='blue'>blue</font> are connected, while sessions in <font color='red'>red</font> are disconnected.

Right-clicking on the selected session will popup a menu allowing you to disconnect/connect, reset, and view the status of the session.

### Messages List ###
All messages allowed on the selected session will be listed on the bottom left corner of the application. Selecting a message will load fields available for that message.

Messages in <font color='blue'>blue</font> are application messages, while messages in <font color='gray'>gray</font> are session/admin messages

Double-clicking on a selected message will launch the browser to the selected message's [FIXwiki](http://fixwiki.org/) page.

### Fields ###
Fields available to a message are shown as a form at the center of the application.

Fields can be filtered to only show required fields. There is also an option whether to modify the header or trailer.

Fields whose names are shown in <font color='blue'>blue</font> are required.

Fields belonging to a message component (FIX 4.3 or later), are displayed under the component name.

Double-clicking on the field name will launch the browser to the selected field's [FIXwiki](http://fixwiki.org/) page.

As of version 1.1, QuickFIX Messenger comes with a feature to send FIX messages in free text form. Note that CheckSum (10) and SendingTime (52) will automatically be populated by QuickFIX/J.

### Messages Table ###
Messages sent or received from the application are logged at the bottom of the application.

Each row of the table represents a FIX message. Rows colored <font color='#FF8040'>orange</font> are received, while rows colored <font color='#669900'>green</font> are sent.

Double-clicking on a row will popup the details of the message.