# Introduction #
<wiki:gadget url="https://goo.gl/Uql18" width="728" height="90" border="0" up\_ad\_client="7386150814279344" up\_ad\_slot="5169503048" up\_ad\_keywords="trading stocks fx bonds" />

QuickFIX Messenger is a front-end messaging application built on-top of the [QuickFIX/J](http://www.quickfixj.org) engine.

It is a tool designed for technical individuals working on the Financial Information eXchange ("[FIX](http://fixprotocol.org/)") Protocol. The FIX Protocol is an industry-driven messaging standard for the electronic communication of trade-related messages.

QuickFIX Messenger is ideal for testing different messages and scenarios on FIX infrastructures. It provides a simple graphical user interface (GUI) for constructing and sending FIX messages across a given FIX session.

For support, questions, or general discussions, kindly visit our [forum](https://groups.google.com/forum/?fromgroups#!forum/quickfix-messenger-discuss).


---





---

# Getting Started #

## Downloading QuickFIX Messenger ##
QuickFIX Messenger can be downloaded as an executable binary or can be built from source.

Both binary and source distributions are available for download at [Google Code](http://code.google.com/p/quickfix-messenger/downloads/list)

### Executable Binary ###
Unless planning to make changes to the default distribution, it is recommended to download the executable binary.

The binary distribution file is usually named `qfix-messenger-<version>-bin.zip`.

### Source ###
The source distribution contains an [Eclipse](http://www.eclipse.org/downloads/) project which can be directly imported to an existing Eclipse workspace.

The source distribution file is usually named `qfix-messenger-<version>-src.zip`.

## Running QuickFIX Messenger ##
The binary distribution includes executable scripts for an _Initiator_ instance and an _Acceptor_ instance. Both scripts come in 2 flavors: **`qfix-messenger-<instance>.bat`** for Windows, **`qfix-messenger-<instance>.sh`** for Linux/Unix.

Note that **Java 7 (JRE 1.7)** or later is required to run QuickFIX Messenger.

## Building from Source ##
The source distribution includes an **Ant** script (`build.xml`) which should be used to build QuickFIX Messenger. The default target is `clean.deploy` which will build the project and copy all files to the `deploy` directory.

The `deploy` directory is structured same way as the binary distribution.

Visit our [Developer's Guide](http://code.google.com/p/quickfix-messenger/wiki/DevelopersGuide) for more information.


---

# User's Manual #

## Configuration ##
QuickFIX Messenger comes with 2 sets of configuration files, one for an Initiator instance (`cfg/initiator`), and another for an Acceptor instance (`cfg/acceptor`).

Each instance comes with 3 configuration files:
  * **`log4j.properties`** - Configure logging
  * **`messenger.cfg`** - Configure the messenger application
  * **`quickfix.cfg`** - Configure the QuickFIX engine

### Messenger Configuration ###
  * **`messenger.isInitiator`** - Indicates whether the messenger acts as a connection initiator or not (acceptor)
  * **`messenger.parser.threads`** - Indicates the number of threads to use when parsing a QuickFIX dictionary XML
  * **`messenger.license`** - Indicates the file path to the BSD license
  * **`messenger.icons`** - Indicates the directory path of the icon files
  * **`messenger.home.url`** - Indicates the QuickFIX Messenger website
  * **`messenger.help.url`** - Indicates the QuickFIX Messenger Help website
  * **`messenger.fixwiki.url`** - Indicates the FIXwiki website
  * **`messenger.dict.fix<version>`** - Indicates the file path to the QuickFIX dictionary XML indicated by `version`

### QuickFIX Configuration ###
Please refer to QuickFIX/J's [documentation](http://www.quickfixj.org/quickfixj/usermanual/1.5.1/usage/configuration.html) page for details on how to configure the QuickFIX engine.


---

## User Interface ##
![http://quickfix-messenger.googlecode.com/svn/images/2_0/main.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/main.png)


---

### Creating a Message ###
  1. Select a session from the list; this will display all messages supported by the session's FIX version.
    * If a FIXT session is selected, select the desired `ApplVerID` to use
  1. Select a message from the list; this will display a form containing all fields available to the message.
    * By default, only the required fields are displayed. To change this, unselect the _Required Only_ check box.
    * To show the `Header` fields, select the _Modify Header_ check box.
    * To show the `Trailer` fields, select the _Modify Trailer_ check box.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/options.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/options.png)


---

### Free Text ###
Existing FIX message texts (i.e. from a log file) can be used to send a message. Select _Free Text_ from the message list and paste the message to the text area provided.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/free-text.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/free-text.png)

Note that `CheckSum(10)` and `SendingTime(52)` will automatically be populated/updated by QuickFIX/J.


---

### Repeating Groups ###
For _Repeating Group_ fields, put the desired number of groups and click on _Set_; this is will update the form to display the desired number of groups.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/repeating-group.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/repeating-group.png)


---

### Data Format Verification ###
While QuickFIX Messenger does not support message validation, it does support verification of field data formats. This means that if the input data does not match the expected format defined for the field, a warning symbol will appear on the text field.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/format-check.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/format-check.png)

Because QuickFIX Messenger is designed as a testing tool, fields with incorrect format will not prevent the message from being sent.


---

### Message Actions ###
  * Click on the _shredder_ button to destroy the message and all fields stored in the cache.
  * If an active project is available, click on the _tray_ button to add the message to the project.
  * Click on the _envelope_ button to send the message across the session.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/buttons.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/buttons.png)

If the _Preview Before Sending_ check box is selected, a confirmation will popup before the message gets sent.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/preview.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/preview.png)


---

### Sessions List ###
Active sessions can be managed from the _Sessions List_.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/session-popup.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/session-popup.png)

  * Selecting the _Logon_ check box, initiates a logon sequence to the receiver.
  * Clicking _Reset_ will reset the session' sequence numbers to 1/1.
  * Clicking _Status_ will display the session details.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/session-status.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/session-status.png)


---

### Message Table ###
Messages sent or received are all logged to the _Message Table_.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/message-table.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/message-table.png)

Each row in the table represents a FIX message. Rows colored _orange_ are received, while rows colored _green_ are sent.

Double-clicking on a row will popup the details of the message.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/message-details.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/message-details.png)

To clear the table, right-click then select _Clear All_.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/message-popup.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/message-popup.png)


---

### Project View ###
A separate window is displayed whenever a project is activated (new or open).

![http://quickfix-messenger.googlecode.com/svn/images/2_0/project-view.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/project-view.png)

All messages added to the project are displayed in the window as a tree. Right-clicking on a selected message brings-up a popup menu.

  * **`Load Message`** - Loads the message to the form
  * **`Send Message`** - Sends the message across the session
  * **`Export Message`** - Exports the message as an XML file
  * **`Delete Message`** - Deletes the message from the project
  * **`Send All Messages`** - Sends all messages in the project
  * **`Collapse All`** - Collapses the entire tree
  * **`Expand All`** - Expands the entire tree

At anytime, the Project View window can be activated via _Window_ > _Project Window_ or `CTRL-P`

![http://quickfix-messenger.googlecode.com/svn/images/2_0/project-tree.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/project-tree.png)

Text values can also be modified from tree. Double-click on a text node to enable editing; press _Enter_ to save, _Esc_ to revert.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/project-tree-edit.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/project-tree-edit.png)


---

### Menus ###
#### File Menu ####
![http://quickfix-messenger.googlecode.com/svn/images/2_0/file-menu.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/file-menu.png)

  * **`New Project`** - Creates a new project
  * **`Save Project`** - Saves the active project
  * **`Open Project`** - Opens a project
  * **`Close Project`** - Closes the active project
  * **`Import Message`** - Imports an XML message to the form
  * **`Export Message`** - Exports the form message to an XML file
  * **`Exit`** - Exits the application

#### Session Menu ####
![http://quickfix-messenger.googlecode.com/svn/images/2_0/session-menu.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/session-menu.png)

  * **`All Sessions - Logon`** - Logon all sessions
  * **`All Sessions - Logoff`** - Logoff all sessions
  * **`All Sessions - Reset`** - Reset all sessions

#### Help Menu ####
![http://quickfix-messenger.googlecode.com/svn/images/2_0/help-menu.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/help-menu.png)

  * **`Help`** - Displays this Wiki page
  * **`About`** - Displays the application information, including license

#### Window Menu ####
![http://quickfix-messenger.googlecode.com/svn/images/2_0/window-menu.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/window-menu.png)

  * **`Project Window`** - Opens the _Project View_ of the active project


---

### FIXWiki ###
Double-click on fields in the form or messages in the list to bring-up the corresponding FIXWiki page.


---

# Advanced #
## Custom Logon ##
QuickFIX Messenger supports populating selected fields when sending a `Logon(A)` message.

To do this, modify the QuickFIX/J configuration and add the following attributes under a session configuration:
```
Username=<String>
Password=<String>
RawData=<String>
RawDataLength=<Integer>
TestMessageIndicator=<Boolean>
```

For example:
```
[session]
BeginString=FIX.4.3
SocketAcceptPort=9879
Username=username
Password=password
RawData=test data
RawDataLength=9
TestMessageIndicator=true
```

Note that the configured fields will be populated regardless of the session's FIX version. This means that despite being unsupported, `Username(553)`, `Password(554)`, and `TestMessageIndicator(464)` will still get populated for FIX versions below 4.3.

**Bug**: the application will only apply the custom logon settings if all custom fields are present. As a workaround, include all custom fields in the config and set the unused ones to empty. See [Issue #51](http://code.google.com/p/quickfix-messenger/issues/detail?id=51&can=1&q=milestone%3DRelease2.1).


---

## Save Files ##
QuickFIX Messenger uses XML documents as save files; this allows for a save format that is human-readable and editable from any text editor.

### Message ###
Exported messages are saved in an XML file having a structure similar to the message form.

The schema can be obtained from [Subversion](http://quickfix-messenger.googlecode.com/svn/trunk/qfix-messenger/resources/xsd/message.xsd).

Sample _Message_ XML
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:message xmlns:ns2="http://xml.fix.jramoyo.com" name="NewOrderSingle" msgType="D" isRequiredOnly="true">
    <session>
        <name>FIXT.1.1:INIT&gt;ACCEPT</name>
        <appVersionId>FIX.4.4</appVersionId>
    </session>
    <body>
        <field name="ClOrdID" id="11">12345</field>
        <component name="Instrument">
            <field name="Symbol" id="55">MSFT</field>
        </component>
        <field name="OrdType" id="40">1</field>
        <component name="OrderQtyData">
            <field name="OrderQty" id="38">2400</field>
        </component>
        <field name="Side" id="54">1</field>
        <field name="TransactTime" id="60">20120930-14:20:05.917</field>
    </body>
</ns2:message>
```

### Project ###
Projects are saved in an XML file enclosing multiple Message XMLs.

The schema can be obtained from [Subversion](http://quickfix-messenger.googlecode.com/svn/trunk/qfix-messenger/resources/xsd/project.xsd).

Sample _Project_ XML
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:project xmlns:ns2="http://xml.fix.jramoyo.com" name="Project">
    <messages>
        <message name="NewOrderSingle" msgType="D" isRequiredOnly="true">
            <session>
                <name>FIXT.1.1:INIT&gt;ACCEPT</name>
                <appVersionId>FIX.4.4</appVersionId>
            </session>
            <body>
                <field name="ClOrdID" id="11">12345</field>
                <component name="Instrument">
                    <field name="Symbol" id="55">MSFT</field>
                </component>
                <field name="OrdType" id="40">1</field>
                <component name="OrderQtyData">
                    <field name="OrderQty" id="38">2400</field>
                </component>
                <field name="Side" id="54">1</field>
                <field name="TransactTime" id="60">20120930-14:20:05.917</field>
            </body>
        </message>      
    </messages>
</ns2:project>
```


---

## Changing the "Look and Feel" ##
QuickFIX Messenger uses a cross-platform look and feel provided by [Substance](http://insubstantial.github.com/insubstantial/substance/docs/getting-started.html).

To change this and use the default look and feel provided by the Operating System, modify the script and add the following property to the Java command: `-useSystemLaF=true`

Windows example:
```
javaw -DuseSystemLaF=true -cp %CLASSPATH% com.jramoyo.qfixmessenger.QFixMessenger "cfg\acceptor\messenger.cfg" "cfg\acceptor\quickfix.cfg"
```

Linux/Unix example:
```
java -DuseSystemLaF=true -cp "$CLASSPATH" com.jramoyo.qfixmessenger.QFixMessenger "cfg/acceptor/messenger.cfg" "cfg/acceptor/quickfix.cfg"
```

QuickFIX Messenger running on a Windows 7 look and feel.

![http://quickfix-messenger.googlecode.com/svn/images/2_0/system-laf.png](http://quickfix-messenger.googlecode.com/svn/images/2_0/system-laf.png)