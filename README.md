<!--

author:   André Dietrich; Jihad Hyadi

version:  0.1.0

language: en

comment:  edrys-Lite Documentation

icon:     images/logo.png

narrator: UK English Female

-->

# edrys-Lite Documentation

Welcome to the edrys-Lite documentation!

    --{{0}}--
Edrys-Lite provides an intuitive and simple way for users to engage with laboratory environments directly from their browser -- nearly no servers required.
This documentation will guide you through the process of creating and managing interactive classrooms, developing modules, and exploring the various features of edrys-Lite.
!?[](videos/edrys_01-0.webm)

- 📖 Use the contents below to get started
- 💬 For questions and discussions, please visit our
  [Gitter community](https://gitter.im/edrys-org/community)
- 🐞 For bug reports and feature requests, visit the
  [issues tab](https://github.com/edrys-labs/edrys-lite/issues)
- [![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/edrys-labs/documentation/refs/heads/main/README.md)


## Contents

    --{{0}}--
The first parts of this documentation are for everyone who uses edrys-Lite: teachers who set up a classroom and students who join one.
Background on how edrys-Lite works under the hood, and a guide for developers who want to build their own modules, follow at the end.

**Using edrys-Lite**

1. [Getting Started](#Getting-Started)
2. [Setting up a Classroom](#Setting-up-a-Classroom)
3. [Working in a Classroom](#Working-in-a-Classroom)
4. [Remote Labs with Stations](#Remote-Labs-with-Stations)
5. [Privacy and Security](#Privacy-and-Security)
6. [Troubleshooting](#Troubleshooting)

**Background and Development**

7. [How edrys-Lite Works](#How-edrys-Lite-Works)
8. [Developing Modules](#Developing-Modules)


## Getting Started

    --{{0}}--
Based on [edrys](https://github.com/edrys-org/edrys), edrys-Lite is a lightweight, browser-based implementation designed for remote labs and classrooms.
It enables seamless collaboration by allowing users to create and interact with various modules such as textual and graphical editors, terminals, camera streams, and drawing tools.
The modular architecture ensures that each module operates as an independent entity, making it configurable and reusable across different educational and experimental contexts.
!?[](videos/edrys_03-0.webm)

    --{{1}}--
There is no account to create and nothing to install.
A classroom lives in the browsers of the people who use it, and everyone connects directly to each other.
All you need is a modern browser and the link to a classroom.

      {{1}}
- ✅ No sign-up, no password, no installation
- ✅ Works in Chrome, Edge, Firefox and Safari
- ✅ Classrooms are made of _modules_: editors, terminals, camera streams, task descriptions, ...
- ✅ Remote hardware (e.g. an Arduino) can be shared with students through _stations_

?![YouTube Demo](https://www.youtube.com/watch?v=6ZjGHorc2ds)

### Roles

    --{{0}}--
Everyone in a classroom has one of the following roles. Your role is shown by the icon next to your name in the room list.

| Role        | What they can do                                                                                                   |
| ----------- | ------------------------------------------------------------------------------------------------------------------ |
| **Teacher** | Configure the classroom: settings, modules, members, stations. The creator of a classroom is its _owner_ and always a teacher. |
| **Student** | Join rooms, work with the modules and collaborate with others.                                                     |
| **Station** | A browser left running on a device (e.g. a PC connected to lab hardware) that shows up as its own room.            |
| **Visitor** | Someone who opened the link of a classroom that only admits listed students. Visitors can watch, but cannot change anything. |

    --{{1}}--
With its browser-native design, edrys-Lite provides an accessible and efficient platform for collaborative learning, leveraging modern web technologies to facilitate real-time interaction between students, teachers, and hardware-enabled stations.

### Your User ID

    --{{0}}--
The first time you open edrys-Lite, your browser creates a personal key pair for you.
The public part of this key is your **User ID**. It identifies you in every classroom, and teachers use it to add you as a teacher or student.

    --{{1}}--
To find your User ID, open the menu with the three dots (⋮) in the top right corner.
A short version of the ID is shown there; the copy button next to it copies the full ID, which is what a teacher needs.

      {{1}}
<section>

- Your ID is tied to **this browser**. Another browser, another device, or a private window gives you a different ID.
- Clearing the site data of your browser deletes your ID and the classrooms stored in it. Download a backup of your classrooms first (see [Backup, Restore and Templates](#Backup%2C-Restore-and-Templates)).
- The same menu also lets you switch the language of the interface.

</section>

### Creating a Classroom

*    --{{0}}--
  Visit https://edrys-labs.github.io and click on `Create a class`.
  By the way, the buttons in the footer allow you to have a look at the project on GitHub, read this documentation, explore several ready-to-use remote labs and visit the blog.

       {{0}}
  ![Edrys-Lite](images/edrys-page.png)

*    --{{1}}--
  A new classroom will be generated with a unique ID in the URL, and you are its owner.
  Every new classroom starts with a **welcome guide** in the Lobby, which walks you through the first steps of the setup.
  It is an ordinary Markdown module, so you can edit or delete it at any time in `Settings` → `Modules`.

       {{1}}
  ![Edrys initial classroom](images/edrys-initial-classroom.png)

*    --{{2}}--
  Students who open the classroom before you have set it up see a short note asking them to come back later.

### Inviting People

    --{{0}}--
To invite people, share the classroom link from your browser's address bar.

      {{0}}
```
https://edrys-labs.github.io/?/classroom/<classroom-id>/<owner>
```

    --{{1}}--
The last part of the link identifies you as the owner of the classroom.
Whoever opens the link for the first time uses it to check that the classroom setup they receive really comes from you, so always share the full link.

    --{{2}}--
By default, everyone with the link can join as a student.
If you want to restrict who may take part, add your students to the members list (see [Members](#Members)).

    --{{3}}--
Every classroom you created or joined is listed on the start page, so you can come back to it later.
From there you can open it again, fork it (make your own copy), or delete it from your browser.

      {{3}}
![Index-Page](images/edrys-index.png)


## Setting up a Classroom

    --{{0}}--
Teachers configure the classroom through the `Settings` button next to the classroom name.
The settings are split into the tabs Main, Members, Modules, Stations, Share and Communication.
Changes are applied to everyone in the classroom as soon as you click `Save`.

### Main Settings

    --{{0}}--
In the Main tab you can give your classroom a descriptive title, reference a logo and add a description.
These are also shown in the classroom overview on the start page.

      {{0}}
![Add Meta Information](images/main-settings.png)

    --{{1}}--
The number of rooms defines how many numbered rooms (Room 1, Room 2, ...) the classroom has next to the Lobby.

      {{1}}
<section>

- Raising the number adds the new rooms as soon as you save.
- Lowering it removes the rooms above the new number. People in a removed room are moved back to the Lobby.
- A classroom can have up to 50 rooms.
- The owner can also add a room with the `New room` button at the bottom of the room list.

</section>

### Members

    --{{0}}--
In the Members tab you decide who teaches and who may take part.
Members are added by their User ID (see [Your User ID](#Your-User-ID)), one ID per line.

      {{0}}
![Members Settings](images/members.png)

    --{{1}}--
Teacher IDs get access to the settings, so they can modify the classroom just like you.
The student list works as follows:

      {{1}}
<section>

| Student list             | Who can take part                                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------------------------------- |
| empty, or contains `*`   | Everyone with the classroom link joins as a student.                                                          |
| a list of User IDs       | Only these students (and the teachers) can take part. Everyone else who opens the link becomes a **visitor**. |

</section>

    --{{2}}--
Visitors can follow what happens in the classroom, but whatever they write, send or change is ignored by everybody else.
The members list is checked by every participant's browser, not by a server, so it cannot be bypassed by a modified client.

### Adding Modules

    --{{0}}--
Modules are the building blocks of a classroom: task descriptions, code editors, terminals, camera streams and much more.
Open `Settings` → `Modules` to add them.

    --{{1}}--
Using the Modules Explorer, you can add modules to the classroom by clicking on the `Add` button.
The most frequently used modules are listed first.

      {{1}}
![Add Module from Explorer](images/add-module-0.png)

    --{{2}}--
For more modules, click on the `Explore More` button in the Explorer to see a list of all modules.
Every module comes with a description of its configuration and an __include URL__.
You can copy the URL of a module and paste it into the input field.

      {{2}}
![Add Module](images/add-module-1.png)

    --{{3}}--
Some of the most used edrys modules are:

      {{3}}
- [Markdown-IT](https://github.com/edrys-labs/module-markdown-it): Task descriptions and instructions written in Markdown.
- [Code Editor](https://github.com/edrys-labs/module-monaco-editor): A collaborative code editor that supports multiple languages.
- [PyxTerm.js Terminal](https://github.com/edrys-labs/module-pyxtermjs): A terminal on a station, e.g. to compile and upload the code from the editor.
- [Video Stream](https://github.com/edrys-labs/module-streaming): Streams a camera from a station to the students.
- More modules can be found at: https://github.com/topics/edrys-module

### Configuring Modules

    --{{0}}--
Click on the gear icon next to a module to configure it.
Here you can set its size (width and height), the rooms it appears in, and its content and settings.

      {{0}}
![Configure Module](images/add-module-2.png)

    --{{1}}--
Many modules provide a configuration form with fields, checkboxes and drop-down lists.
Some drop-down lists are presets: picking one fills in the fields below it with suitable values, which you can then adjust.
If you prefer, you can switch to the advanced view and edit the raw configuration as YAML or JSON.

      {{1}}
![Module Configuration Form](images/add-module-3.png)

    --{{2}}--
Settings can be given for everyone (`config`), or separately for students, teachers and stations.
If a module's configuration contains an error, its gear icon turns into a warning sign.

    --{{3}}--
You can drag and drop modules to rearrange them. In the list, modules are grouped by the rooms they appear in.

#### Show in

    --{{0}}--
The `Show in` field decides in which rooms a module appears. It is a comma separated list of the following entries:

<section>

| Entry          | Shows the module in                                     |
| -------------- | ------------------------------------------------------- |
| `*`            | every room (default)                                    |
| `lobby`        | the Lobby                                               |
| `station`      | every station room                                      |
| `Room 1`       | exactly this room (`Room 1` does not include `Room 10`) |
| `Room *`       | every room whose name starts with `Room `               |
| `teacher-only` | combined with the above: only for teachers              |
| `station-only` | combined with the above: only on the station itself     |

</section>

    --{{1}}--
For example, `lobby, Room 1, Room 2` shows a module in the Lobby and the first two rooms, and `station, station-only` shows it only to the station device, e.g. for a hardware connection that students should not see.
If no module is configured for a room, the room shows a short note instead.


### Backup, Restore and Templates

    --{{0}}--
There is no central server that stores your classroom: it lives in your browser and in the browsers of the people who use it.
Open `Settings` → `Share` to download a backup of your classroom, or to restore one.
Download a backup now and then, and always before you clear your browser data.

![Load Config](images/load-config.png)

    --{{1}}--
You can download the configuration as a JSON or YAML file, whereby we prefer YAML for its better readability.
The result looks similar to the following example, which can be modified manually or shared with others.

     {{1}}
```yaml
id: unique id of the lab
dateCreated: date of creation
name: name of the lab
meta:
  logo: url of the lab logo
  description: description of the lab
  defaultNumberOfRooms: number of rooms
members:
  teacher: list of teacher ids
  student: list of student ids
modules:
  - url: url of the module
    config: available for everyone
    studentConfig: available for students
    teacherConfig: available for teachers
    stationConfig: available in stations
    showInCustom: rooms in which the module will be shown
    width: full/half/third (or a custom value)
    height: huge/tall/medium/short (or a custom value)
```

    --{{2}}--
The file contains no keys or signatures.
Whoever restores it becomes the owner of the restored classroom, so a file can be shared freely as a template.

    --{{3}}--
You can restore a configuration either from your local file system or, if it is hosted somewhere on the web, by pasting the URL of the file.

    --{{4}}--
Some ready-to-use classroom configurations are available in the following repositories (you can also just click the deploy button of the desired configuration):

      {{4}}
https://github.com/topics/edrys-lab

    --{{5}}--
Deploy buttons are a shortcut to create a new classroom from a configuration file. The only relevant part is the URL of the file, which is appended to `https://edrys-labs.github.io/?/deploy/`.
This instructs edrys-Lite to create a new classroom with the configuration fetched from the given URL.

      {{5}}
```markdown
[fast deploy](https://edrys-labs.github.io/?/deploy/https://raw.githubusercontent.com/edrys-labs/lab-web-serial/main/laboratory/micropython.yaml)
```

    --{{6}}--
You can try this out by yourself by clicking on the following button:

      {{6}}
[<img src="https://img.shields.io/badge/%F0%9F%9A%80%20-%20Deploy%20Lab%20-%20light?style=plastic" height="25" />](https://edrys-labs.github.io/?/deploy/https://raw.githubusercontent.com/edrys-labs/lab-web-serial/main/laboratory/micropython.yaml)


### Communication

    --{{0}}--
By default, edrys-Lite connects everyone directly to each other via WebRTC. However, under certain network conditions, such as strict firewalls or NATs at schools and universities, WebRTC may not work reliably.

    --{{1}}--
In such cases, you can switch to a WebSocket connection in `Settings` → `Communication`. All messages are then relayed through a WebSocket server.

    {{1}}
![Change Communication Protocol](images/communication-ws.png)

    --{{2}}--
For both methods you can optionally change the server settings, such as the signaling server and the STUN/TURN servers for WebRTC, or the WebSocket server URL. If you leave them empty, the defaults are used.

    {{2}}
![Change Communication Protocol](images/communication-webrtc.png)

    --{{3}}--
Everyone in a classroom has to use the same settings to find each other.
The Communication tab therefore shows a share link that contains these settings; send this link to your students instead of the plain classroom link.
If you tick the option to keep the settings in the URL, your own address bar shows this link as well.


## Working in a Classroom

    --{{0}}--
Once you have joined a classroom, the side menu on the left lists its rooms and who is in them.
Click on a room to move there. Everyone starts in the Lobby.

    --{{1}}--
The modules of a room are shared by everyone in it: if one student types into an editor, the others see it right away, together with each other's cursors.
Each room has its own state, so different groups can work in different rooms without interfering.

      {{1}}
<section>

- **Room list:** Each person is shown with an icon for their role (teacher, student, station, visitor). Your own name is highlighted.
- **Chat:** The chat button in the top bar opens the classroom chat. A badge tells you when new messages have arrived. Messages can be formatted with Markdown.
- **Connection:** If your connection to the classroom is lost, a `Reconnecting…` notice appears in the top bar. edrys-Lite reconnects by itself.

</section>


## Remote Labs with Stations

    --{{0}}--
Edrys-Lite stations enable remote labs, automated grading, and other experiences where an automated or hardware-based interaction is required.
A station is simply an instance of an edrys-Lite classroom running in "station mode" and left open to handle student interactions.
The functionality of a station is determined by the modules loaded within it.

    --{{1}}--
Stations can run on any device with a browser, including servers, laptops, Raspberry Pis, or even always-on smartphones.

### Opening a Station

    --{{0}}--
In `Settings` → `Stations` you find the station link of your classroom. Open it on the device that should become the station (only a teacher can open a station).
The link looks like the classroom link, but contains `station` instead of `classroom`, so the browser knows that it has to operate in station mode.

![Station](images/station-settings.png)

    --{{1}}--
The station appears as a separate room in the classroom, and students can interact with it by clicking on the room.
Every station also has its own user, which is shown in the room list. Changing the station name also changes this user name.
You can open multiple stations in parallel on different devices to make several hardware resources available.

      {{1}}
![Station](images/stations.png)

    --{{2}}--
A station keeps working while its tab is in the background, so the device can be used for other things in the meantime.
When the station tab is closed, its room disappears from the classroom after a few seconds and the students in it are moved back to the Lobby.
If the station only reloads, it comes back in the same room and the students stay.

### Example: Arduino Remote Lab

    --{{0}}--
An example use case of stations is a remote Arduino lab, where students can remotely interact with an Arduino (upload code to it and see the result through a camera) that is physically hosted somewhere else (e.g. on university grounds).
In this example, a university would like to give its students remote access to its fleet of lab devices, removing any need for students to be physically present to experiment with them.

    --{{1}}--
To achieve this, each Arduino is connected to a computer with internet access (in this example a Raspberry Pi), and a station is opened in each computer's browser.
We can use a USB webcam with the [Station-Stream](https://github.com/edrys-labs/module-streaming) module to let students see the Arduino, the [Code Editor](https://github.com/edrys-labs/module-monaco-editor) module to let students write code, and the [PyxTerm.js Terminal](https://github.com/edrys-labs/module-pyxtermjs) module to compile and upload it, which needs a small server running locally to connect the Arduino to the browser.

      {{1}}
1. [Station-Stream](https://github.com/edrys-labs/module-streaming)
2. [Code Editor](https://github.com/edrys-labs/module-monaco-editor)
3. [PyxTerm.js Terminal](https://github.com/edrys-labs/module-pyxtermjs)

    --{{2}}--
The overall setup for one station could look like this:

      {{2}}
<div align="center">
<img src="images/arduino-lab.png"/>
</div>

    --{{3}}--
Overall, this allows an easy setup of remote labs without configuring security, servers, port forwarding, or any other infrastructure.
All that is needed is a running browser, which can be repeated for any number of stations.
This produces a portable, scalable, and easy-to-share setup that can be replicated even by non-technical teachers.
The same principles apply to any other lab devices, since modules can be reused, combined, or developed to accommodate any setup.


## Privacy and Security

    --{{0}}--
Edrys-Lite works without user accounts and without a central server that stores your data. Instead, trust is built on the keys that every browser creates for its user.

<section>

- **No tracking:** There is no sign-up, no password, and no data collection. Classrooms are stored in the browsers of their participants.
- **Signed changes:** The classroom setup, the rooms, the chat and who is present are signed with the key of their author. Every participant's browser checks these signatures and ignores anything that was not signed by someone allowed to make that change.
- **Owner check:** The owner part of the classroom link lets a newcomer verify that the setup comes from the real owner.
- **Members list:** Only teachers can change the setup. If you list your students, nobody else can take part (see [Members](#Members)).
- **Safe content:** Chat messages and descriptions are shown as text, so they cannot run code in other people's browsers. Modules run isolated from the classroom page.

</section>

    --{{1}}--
Keep in mind that everyone who is allowed to work in a room can change the content of its modules, just as everyone in a real classroom can write on the whiteboard.


## Troubleshooting

<section>

**Others don't show up, or the classroom stays empty**

Your network probably blocks direct WebRTC connections. Switch to WebSocket in `Settings` → `Communication` and share the new link from that tab (see [Communication](#Communication)).

**A student cannot change anything**

The student is a visitor: the members list contains students, but not this one. Add their User ID, or empty the student list to let everyone in.

**A module does not appear in a room**

Check the `Show in` field of the module (see [Show in](#Show-in)). Room names must match as a whole: `Room 1` does not include `Room 10`.

**A station room disappeared**

The station tab was closed or its device lost its connection. Open the station link on the device again.

**My classroom is gone**

Classrooms are stored in the browser. A different browser, a private window, or cleared site data starts empty. Restore your classroom from a backup (see [Backup, Restore and Templates](#Backup%2C-Restore-and-Templates)).

</section>


## How edrys-Lite Works

    --{{0}}--
This section explains the technologies behind edrys-Lite. You don't need to know them to use edrys-Lite, but they help to understand why it works without a server.

### Principles and Technologies

    --{{0}}--
As you have seen, edrys-Lite employs a modular approach where each module can be interconnected to facilitate interaction and communication among users.
Two mechanisms connect them: messages, which are sent directly to the other people in a room, and a shared state, which is kept in sync by Conflict-Free Replicated Data Types (CRDTs).
The participants' browsers are connected directly via WebRTC, or through a WebSocket relay where WebRTC is blocked.

### WebRTC Communication

>    --{{0}}--
> The Web Real-Time Communication is a free and open-source project providing web browsers and mobile applications with real-time communication (RTC) via application programming interfaces (APIs).
> It allows audio and video communication to work inside web pages by allowing direct peer-to-peer communication, eliminating the need to install plugins or download native apps...
> !?[](videos/edrys_05-0.webm)
>
> _Source: [Wikipedia](https://en.wikipedia.org/wiki/WebRTC)_


    {{0-1}}
``` ascii
                     (WebRTC)
Alice 👩‍💻 <------------------------------> 👨🏾‍💻 Bob
```

    --{{1}}--
But the entire process is actually a bit more complicated. At first, Alice initiates the WebRTC connection by generating an SDP offer that details her media capabilities, such as the types of audio and video streams she supports, along with the associated codecs and network parameters. This offer is then sent to the signaling server, which acts solely as a relay for connection setup information.
!?[](videos/edrys_05-1.webm)

    --{{2}}--
The signaling server receives Alice’s offer and forwards it to Bob. This intermediary role is crucial because it allows the initial exchange of connection data even when both parties are behind NATs or firewalls, ensuring that they can communicate the necessary parameters without directly connecting first.
!?[](videos/edrys_05-2.webm)

    --{{3}}--
After Bob receives Alice’s offer through the signaling server, he generates an SDP answer that outlines his media capabilities and confirms the proposed connection parameters. This answer provides a mutual understanding of the media exchange, indicating that Bob is ready to establish a connection and detailing his own network settings.
!?[](videos/edrys_05-3.webm)

    {{1}}
``` ascii
               (Signaling Server)

       .-------------> 🖥️ --------------.
       |    "{1}{}"   /  A      "{2}{}" |
       |             /    \             |
       |            /      \            V
                   /        \
Alice 👩‍💻 <--------'          '--------- 👨🏾‍💻 Bob
            "{4}{}"             "{3}{}"
      A                                  A
      |                                  |
      '----------------------------------'
      A    "{5}{Direct Communication}"   A
      |                                  |
      '-- - - - - - - - - - - - - - - - -'
             "{6}{InDirect via TURN}"
```

    --{{4}}--
The signaling server then relays Bob’s SDP answer back to Alice. This step completes the signaling handshake, allowing both peers to possess the required session descriptions that enable them to move forward with establishing a direct connection.
!?[](videos/edrys_05-4.webm)

    --{{5}}--
With the SDP offer and answer exchanged, Alice and Bob proceed with the ICE (Interactive Connectivity Establishment) process, wherein they gather potential network paths and perform connectivity checks. If successful, this process establishes a direct peer-to-peer connection that is optimized for low latency and secure real-time communication.
!?[](videos/edrys_05-5.webm)

    --{{6}}--
If the direct connection attempt fails due to restrictive NATs or firewalls, the process falls back to using a TURN server. In this case, the TURN server relays media traffic between Alice and Bob, ensuring that the communication remains uninterrupted, even though it might introduce a bit more latency compared to a direct connection.
!?[](videos/edrys_05-6.webm)


    {{7}}
> More confusing information on WebRTC:
>
>     --{{7}}--
> Simply listen to another explanation on YouTube:
> !?[](videos/edrys_05-7.webm)
>
> !?[WebRTC](https://www.youtube.com/watch?v=7cbD-hFkzY0)

    --{{8}}--
In edrys-Lite, the connections between participants carry data, not audio or video: the classroom state, messages and presence travel over WebRTC data channels. Only camera streams of modules use WebRTC media connections, which are set up separately by the streaming module.
A TURN server is only used if one is configured; you can add your own in [Communication](#Communication).

    --{{9}}--
If WebRTC is blocked entirely, a classroom can use a WebSocket server instead (see [Communication](#Communication)). The server then relays the messages between the participants, but the signatures described in [Privacy and Security](#Privacy-and-Security) are still checked by every browser.

### State Synchronization

    --{{0}}--
A _**C**onflict-free **R**eplicated **D**ata **T**ype_ (CRDT) is a new type of data structure[^1] that can be replicated across multiple instances in a network with the following guarantees:
!?[](videos/edrys_06-0.webm)

    {{1}}
1. A replica can be updated independently, concurrently and without coordinating with other replicas.
2. Inconsistencies can be resolved automatically.
3. Although replicas may have different state, they are guaranteed to eventually converge.

    --{{1}}--
CRDTs allow each replica to be updated independently and concurrently without needing to coordinate with other replicas, meaning that changes can be made even when devices are disconnected or operating in parallel. Any inconsistencies that arise from these independent updates are automatically resolved by the system, ensuring that differences are managed seamlessly. Even though replicas might temporarily have different states, the underlying design guarantees that they will eventually converge to a consistent state once all updates are shared.
!?[](videos/edrys_06-1.webm)


      {{2}}
__Task:__ Implement a distributed counter

    --{{2}}--
The following example is used only as an illustration of the problem that CRDTs solve. In practice, CRDTs are used to implement more complex data structures, such as sets, maps, and lists, that can be replicated across multiple devices in a network.
!?[](videos/edrys_06-2.webm)

    --{{3}}--
In this distributed counter, both Alice and Bob start with a value of 0. Bob first adds 5 to his counter, and his update is transmitted to Alice so that her counter also reflects a value of 5. Next, Alice increments her counter by 1, raising her local value to 6; however, if this update fails to reach Bob, he remains unaware of the change and retains his previous value of 5. Later, when Bob adds 2 to his counter, his value increases to 7, creating a divergence between the two replicas. The conceptual problem here is that without the reliability and conflict-resolution guarantees provided by CRDTs, lost messages—like Alice’s +1—result in inconsistent states, as the replicas no longer converge on a single, agreed-upon counter value.
!?[](videos/edrys_06-3.webm)

    {{3}}
``` ascii
Alice 👩‍💻

[0]---------*-->[5]--[+1 = 6]--------*-->[8]-- - - - - - - - - - - - 
           /            \           /          \
          A              V         A            \
         /                        /              \
[0]---[+5 = 5]-----------------[+2 = 7]-- - - - --*- - - - - - - - - -

Bob 👨🏾‍💻
```

    {{4}}
__Solution:__ Let every replica count its own part...

    --{{4}}--
How can the same problem be solved for a network with messages losses, fluctuating users and no central authority.
!?[](videos/edrys_06-4.webm)

    --{{5}}--
In this CRDT-based approach, every replica only ever changes its own entry: the total of everything it has added itself. Alice starts with (a,0) and Bob with (b,0); Bob's +5 makes his entry (b,5), Alice's +1 makes hers (a,1), and Bob's +2 makes his (b,7).
Instead of single increments, each message carries the sender's complete state. A receiver merges it by keeping, for every entry, the larger value, and the counter's value is the sum of all entries.
If a message is lost, like Alice's (a,1), the next one she sends contains it again. Merging the same state twice changes nothing, and the order of messages does not matter, so both replicas converge on the same value, here 1 + 7 = 8.

    {{5}}
``` ascii
Alice 👩‍💻

{(a,0)}----------*-->{(a,0),(b,5)}->{(a,1),(b,5)}---*-->{(a,1),(b,7)}
                /                         \        /   
               A                           V      A   
              /                                  /
{(b,0)}---{(b,5)}----------------------------{(b,7)}-----------------

Bob 👨🏾‍💻
```

    {{6}}
<section>

__Implementations__

   --{{6}}--
There are several libraries and frameworks that provide CRDT implementations for various data structures, including sets, maps, and lists. We use Yjs, a popular CRDT library that offers shared maps, arrays and text, and that does not depend on a particular network: edrys-Lite synchronizes it over WebRTC or WebSocket.


- [Automerge](https://automerge.org)
- [__Yjs__](https://docs.yjs.dev)

</section>


[^1]: The CRDT concept was defined in 2011 by Marc Shapiro, Nuno Preguiça, Carlos Baquero and Marek Zawirski.

      See also: https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type

### How edrys-Lite Puts It Together

    --{{0}}--
Every classroom is one shared Yjs document, of which every participant's browser holds a full copy. Besides it, edrys-Lite uses two kinds of information that are not stored.

<section>

| What                  | How it is shared                                                                                     | Kept?                                       |
| --------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| Classroom setup       | Yjs document, signed by the owner or a teacher                                                       | yes, in every participant's browser         |
| Rooms and module state | Yjs document, one shared map per room (what modules store with `Edrys.getState`)                    | yes                                         |
| Chat                  | Yjs document, every message signed by its author                                                     | yes                                         |
| Who is present, and where | Yjs _Awareness_: short-lived, signed entries that every browser renews regularly               | no, an entry disappears when its user leaves |
| Module messages       | sent directly to each person in the room, signed for sender, room and addressee                     | no                                          |

</section>

    --{{1}}--
Because every browser holds the whole document, a classroom keeps working as long as one participant is online, and newcomers receive it from whoever is there.
There is no server that could decide what is correct, so every browser checks the signatures itself and ignores what was not signed by someone allowed to make that change (see [Privacy and Security](#Privacy-and-Security)).


## Developing Modules

    --{{0}}--
Edrys labs are based on the concept of "modules".
A module is a classroom/lab building block.
You can create your own modules or explore existing modules and add them to your classroom.

    --{{1}}--
A module is just an HTML page that is run in an iframe and shown to your students, teachers, and on stations.
You can make the module behave differently depending on where it is currently loaded.
Modules use the Edrys.js library to send and receive messages in real time, allowing you to build any live functionality without setting up any real-time infrastructure, authenticating users, or configuring anything else, as that is all handled upstream by Edrys.

      {{1}}
<!-- data-marker="14 0 14 200 log" -->
``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <meta
      name="description"
      content="A reference module to help with development"
    />
    <meta name="show-in" content="*" />
    <title>Reference Module</title>

    <script src="https://edrys-labs.github.io/module/edrys.js"></script>
   ...
```

    --{{2}}--
You can also inspect the reference module, which is a good starting point for developing your own modules.
It shows how to use the edrys.js library and how to interact with the environment to send and receive messages, update the state.

      {{2}}
https://github.com/edrys-labs/module-reference/blob/main/index.html


    --{{3}}--
You can also explore existing ready-to-use modules, check out the:

      {{3}}
[`edrys-module` tag on GitHub](https://github.com/topics/edrys-module).

    --{{4}}--
A module only accepts messages from the edrys-Lite page that embeds it. Messages that other windows post to it, such as frames the module opens itself, are ignored by edrys.js.


### `edrys.js`

    --{{0}}--
The Edrys JavaScript client library provides an interface to interact with Edrys live classrooms.
It includes reactive properties and various functions to manage messaging, updates, and local storage.

#### Properties

    {{0}}
<section>

##### `Edrys.ready`

__Boolean indicating if Edrys is initialized.__

    --{{0}}--
This boolean property indicates whether the Edrys system has finished initializing and is fully prepared to manage module interactions, ensuring that all functionalities are available before executing module-specific operations.

```js
console.log(Edrys.ready); // true or false
```

---

</section>

    {{1}}
<section>

#### `Edrys.role`

__User role within the classroom.__

    --{{1}}--
This property specifies the current user's role within the classroom environment -- whether they are a teacher, student, or station -- enabling the system and modules to adapt their behavior based on the user's access level and responsibilities.

```js
console.log(Edrys.role); // "teacher", "student", or "station"
```

---

</section>

    {{2}}
<section>

#### `Edrys.username`

__The ID of the current user.__

    --{{2}}--
This property holds the identifier of the current user in the classroom. It is the key under which the user is listed in `Edrys.liveClass.users`, and the value you pass to `Edrys.sendMessage` to address a single user.


```js
// Current user's ID
console.log(Edrys.username);
```

---

</section>

    {{3}}
<section>

#### `Edrys.module`

__Users of the module can pass in some run-time configuration to your module to customize its behavior.__

    --{{3}}--
This object contains the runtime configuration for a module, including general settings and role-specific options (for students, teachers, or stations), allowing the module to adjust its behavior dynamically based on the context in which it is used.

```js
// Always available
console.log(Edrys.module.config);
// Only available when this module is loaded to a student
console.log(Edrys.module.studentConfig);
// Only available when this module is loaded to a teacher
console.log(Edrys.module.teacherConfig);
// Only available when this module is loaded on a station
console.log(Edrys.module.stationConfig);
```

---

</section>

    {{4}}
<section>

#### `Edrys.liveClass`

__Reactive object representing the live classroom state.__

    --{{4}}--
This reactive state object represents the overall classroom environment by providing real-time information about the users who are currently present and the available rooms, which enables modules to update and respond dynamically as the classroom state changes.

```js
// Users currently present in the classroom, keyed by their ID:
// { "<id>": { displayName, room, role }, ... }
console.log(Edrys.liveClass.users);
// Rooms of the classroom, keyed by room name, each with the shared
// state of its modules: { "Lobby": { ... }, "Room 1": { ... }, ... }
console.log(Edrys.liveClass.rooms);
```

---

</section>

    {{5}}
<section>

#### `Edrys.liveRoom`

__Reactive object representing the live room state.__

    --{{5}}--
This reactive object holds the shared state of the current room, i.e. everything the modules in this room stored with `Edrys.getState`, as a plain object. It does not contain the room's name; that is `Edrys.liveUser.room`.

```js
// Shared state of the current room, keyed by state key
console.log(Edrys.liveRoom);
// Name of the current room
console.log(Edrys.liveUser.room);
```

---

</section>

    {{6}}
<section>

#### `Edrys.liveUser`

__Reactive object representing the live user state.__

    --{{6}}--
This reactive state object stores personalized data about the current user, such as their display name and the room they are occupying. It can be undefined for a moment while the user is joining, so check it before use.

```js
// User's display name
console.log(Edrys.liveUser?.displayName);
// User's current room
console.log(Edrys.liveUser?.room);
// User's role: "teacher", "student" or "station"
console.log(Edrys.liveUser?.role);
```

---

</section>

    {{7}}
<section>

#### `Edrys.debug`

__Enable or disable debug messages in the console.__

    --{{7}}--
This flag enables or disables the logging of debug messages to the console, assisting developers by providing real-time diagnostic information to help troubleshoot and monitor the internal operations of the system.

```js
// Import the debug function to log messages (instead of console.log, console.warn, etc)
const dbg = Edrys.importDebug();
// Disable debug messages (or true to enable them)
Edrys.debug = false;
// Log a debug message
dbg('Survey Module Ready');
```

---

</section>

    {{8}}
<section>

#### `Edrys.class_id`

__The ID of the classroom.__

    --{{8}}--
This property holds the unique ID of the classroom the module is loaded in, the same ID that appears in the classroom link. Use it to tell classrooms apart, for example as part of a key when your module stores data outside of edrys.

```js
console.log(Edrys.class_id);
```

</section>

#### Event Handling

    --{{0}}--
The Event Handling section details how modules can register callback functions to respond to important system events.
These methods let you execute custom code when the Edrys system is fully initialized or when any real-time state updates occur, ensuring that your module remains synchronized with the dynamic classroom environment.

      {{1}}
<section>

##### `Edrys.onReady(handler)`

__Register a handler to be called when Edrys is ready.__

    --{{1}}--
This method allows you to register a callback function that will be executed once the Edrys system has fully loaded and is ready to handle module interactions. The handler runs only once, so it is the right place for one-time setup such as creating an editor.

```javascript
Edrys.onReady(() => console.log("Module is loaded!"));
```

</section>

      {{2}}
<section>

##### `Edrys.onUpdate(handler)`

__Register a handler to be called on any real-time state changes.__

    --{{2}}--
This function enables you to set up a callback that will be triggered on any real-time state changes within the classroom environment, allowing your module to respond dynamically to updates as they occur.

```javascript
Edrys.onUpdate(() => console.log("Module is updated!"));
```

</section>

#### Messaging

    --{{0}}--
Modules can send and receive messages in real time.
Messages are sent to a specific user only or to all users in __the same room__.
Every message is signed for its sender, room and addressee, so a received message really comes from the user in `from`, and messages from visitors are not delivered.

      {{1}}
<section>

##### `Edrys.sendMessage(subject, body, user?)`

    --{{1}}--
This method enables modules to send messages in real time by specifying a subject and a body. The body, which can be of any type, is automatically handled through serialization and deserialization, ensuring smooth data exchange. Optionally, you can target a specific user by providing their identifier, otherwise the message is broadcast to all users in the same room.

- Sends a message with the given subject and body.
- The body can be of any type, this will be automatically serialized and deserialized by using [msgpackr](https://github.com/kriszyp/msgpackr).
- user(optional): the user to send the message to, this is the `from` field when receiving the message with the `onMessage` handler.

```javascript
Edrys.sendMessage("subject", "body");
```

---

</section>

      {{2}}
<section>

##### `Edrys.onMessage(handler, promiscuous?)`

    --{{2}}--
This function allows you to register a callback that listens for incoming messages. The handler receives an object with the sender’s details, the subject, and the message body whenever a new message is received. By setting the promiscuous flag to true, the handler can capture all messages in the room, while leaving it false limits the scope to messages intended specifically for the current module.

- Registers a handler for receiving messages.
- `handler({ from, subject, body })`: Called when a message is received.
- `promiscuous`: If true, listens to all messages in the room; otherwise, only listens to messages sent by the same module (same module URL).
- Returns a function that removes the handler again.

``` javascript
const stop = Edrys.onMessage(({ from, subject, body }) => {
  console.log("Got new message: ", from, subject, body);
});

// later: stop listening
stop();
```

</section>

#### Local Storage

    --{{0}}--
Modules can store data locally to persist state across sessions within the browser.

    {{1}}
<section>

##### `Edrys.setItem(key, value)`

__Stores a value in local storage, scoped to the current class and user room.__

    --{{1}}--
This method allows modules to save data locally within the browser, storing a specific value under a given key. The data is scoped to the current class and user room, ensuring that the information persists across sessions and remains isolated within the appropriate context.

``` javascript
Edrys.setItem("key", "value");
```

---

</section>

    {{2}}
<section>

##### `Edrys.getItem(key)`

__Retrieves a stored value from local storage.__

    --{{2}}--
This function retrieves data that was previously stored in local storage using the specified key. It enables modules to access persisted state across browser sessions, ensuring a consistent experience for users within the same classroom and room context.

```javascript
Edrys.getItem("key");
```

</section>

#### State Management

    --{{0}}--
Edrys.js initializes by listening to message events from its parent frame and sets up reactive state management using Yjs.
It therefore uses the same datatypes as Yjs.
The state is kept per room: every room has its own copy, shared by everyone in it.

Yjs documentation: https://docs.yjs.dev/api/shared-types

    {{1}}
<section>

##### `Edrys.getState(key?, type?, value?)`

    --{{1}}--
This method retrieves or initializes a reactive state entry using Yjs data structures, such as Map, Array, or Value, enabling modules to share and synchronize state across clients.

- Retrieves or initializes a state entry.
- type: Can be one of `Map`, `Array`, `Text`, `XmlFragment`, `XmlText`, `XmlElement`, `Value`, or `Awareness`.
- If type is Value, an optional value can be provided: with a value the entry is set, without one the current value is returned.
- Without a key, the whole state of the current room is returned (a `Y.Map`).

```javascript
const state = Edrys.getState("key", "Map");

// set two values in the map
state.set('option1', 12)
state.set('option2', [12 , 22, true])

// get the value of option1
console.log(state.get('option1')) // 12

// get the entire map
console.log(state.toJSON())
// Object { option1: 12, option2: [12, 22, true] }
```

---

</section>

    {{2}}
<section>

##### Awareness (cursors and presence)

    --{{2}}--
With the type `Awareness`, `getState` returns a Yjs [Awareness](https://docs.yjs.dev/api/about-awareness) object for the current room and key.
Awareness is meant for short-lived information that should not be stored, such as cursors, selections or who is currently typing. Editor bindings like `y-monaco` or `y-codemirror` accept it directly.

- Call it from within `Edrys.onReady()`; before that it throws.
- Each room and key has its own awareness, so the cursors of different editors or rooms don't mix.
- A user's states are removed automatically when they leave the room or the module is reloaded.

```javascript
Edrys.onReady(() => {
  const text = Edrys.getState("code", "Text");
  const awareness = Edrys.getState("code", "Awareness");

  awareness.setLocalStateField("user", {
    name: Edrys.liveUser?.displayName,
    color: "#ff8800",
  });

  awareness.on("change", () => {
    // everyone's state in this room, keyed by client id
    console.log(awareness.getStates());
  });

  // e.g. new MonacoBinding(text, editor.getModel(), new Set([editor]), awareness)
});
```

---

</section>

    {{3}}
<section>

##### `Edrys.updateState(transaction : () => {})`

    --{{3}}--
Since every state update will trigger the `Edrys.onUpdate` handler, this function batches multiple state updates into a single transaction, ensuring that changes are applied together and trigger only one update event, thereby improving performance and consistency.

```javascript
const state = Edrys.getState("key", "Map");

Edrys.updateState(() => {
  state.set('option1', 12)
  state.set('option2', [12 , 22, true])
  state.set('option3', "a string")
});
```

---

</section>

    {{4}}
<section>

##### `Edrys.clearState(key)`

__Removes a state entry from the current room.__

    --{{4}}--
This method removes a specific state entry from the current room, effectively clearing any persisted data associated with the given key and keeping the reactive state clean.

```javascript
Edrys.clearState("key");
```

</section>

#### Streaming

    --{{0}}--
A module can also share a stream of data. This can be used to share video, audio... with other users in the room.

    {{1}}
Streams can be shared by either using WebRTC or WebSockets. It is recommended to use WebRTC for real-time streaming, as it provides better performance and lower latency.
WebRTC streams use the STUN/TURN servers configured for the classroom.
If WebRTC is not available, you can use a WebSocket relay as a fallback.

    {{1}}
Only members in the station's room receive a stream: a viewer is connected only after it asked for the stream through a signed edrys message, and a WebSocket stream uses a random relay room that is handed out the same way.

    {{2}}
<section>

##### `Edrys.sendStream(stream, options?)`

__Sends a stream to all users in the room.__

    --{{2}}--
This method transmits a media stream, such as video or audio, to all connected users in the current room.
You can configure the streaming method and WebSocket URL through the optional options parameter.

- `options.method`: `"webrtc"` (default) or `"websocket"`.
- `options.websocketUrl`: the relay server, for `"websocket"`.
- `options.streamName`: tells several streams of one station apart; defaults to `stationConfig.streamName`, then `"Camera 1"`.
- `options.peerServerConfig`: a custom PeerJS server for `"webrtc"`; defaults to `stationConfig.peerServerConfig`.
- Resolves to `{ stop(), updateStream(newStream) }`.

```javascript
navigator.mediaDevices
    .getUserMedia(constraints)
    .then(async (stream) => {
      videoElement.srcObject = stream;
      videoElement.autoplay = true;
      loaderElement.classList.add("hidden");

      currentStream = await Edrys.sendStream(stream, {
        method: streamMethod,
        websocketUrl: websocketUrl,
      });
    })
```

---

</section>

    {{3}}
<section>

##### `Edrys.onStream(handler, options?)`

__Registers a handler for receiving streams.__

    --{{3}}--
This function registers a callback to handle incoming media streams from other users in the room.
The handler receives the stream object and associated settings when a new stream is received, allowing your module to process, display, or manipulate the incoming media content.

- `handler(stream, settings, metadata)`: `settings` is the station's `stationConfig`, `metadata` is `{ streamName, room }`.
- `options`: the same `method`, `websocketUrl`, `streamName` and `peerServerConfig` as for `sendStream`; both sides must use the same method and stream name.
- Resolves to `{ stop() }`.

```javascript
Edrys.onStream((stream, settings) => {
    videoElement.srcObject = stream;
    applyVideoTransform(videoElement, settings);
}, {
    method: streamMethod,
    websocketUrl: websocketUrl,
}).then((stream) => {
    currentStream = stream;
});
```

</section>

### Metadata

    --{{0}}--
Edrys scrapes module HTML files for metadata. It looks at meta tags in your HTML
and stores this information. The following meta tags can be set:

- `title`: \
  the page title tag will be used as the module name

- `description`: \
  module description that will be shown to people adding your module.
  It is shown as plain text: line breaks (`<br>`) and `http(s)` links (`<a href="...">`) are kept, all other HTML is removed.

- `show-in`: \
  defines where the module will be shown by default.
  It accepts the same entries as the `Show in` field of the module settings (see [Show in](#Show-in)), e.g. `*`, `lobby`, `station` or room names.

- `fetch`: \
  this cannot be used for every module, but it allows to fetch the index.html directly without the need of hosting.
  This is especially useful for modules that might change in the future, but you want to have a stable version.
  Hence, you can use the URL to a tagged version on GitHub, which will not destroy other experiments if the module configuration changes.
  Such modules are inlined and run on a `data:` URL, i.e. with an opaque origin.

  Checkout the Markdown-It module on: https://github.com/edrys-labs/module-markdown-it

- `module-config`: \
    a JSON object that is passed to edrys which will then create a simple form to configure the module.
    The form fields are dynamically generated based on the schema provided. An example of a schema can be found in the [Markdown-It module (html head)](https://github.com/edrys-labs/module-markdown-it/blob/main/index.html#L15).

#### Module Configuration Schema

    --{{0}}--
The schema has one entry per configuration type (`config`, `studentConfig`, `teacherConfig`, `stationConfig`), each listing its fields.
Every field has a `type`, and optionally a `hint` shown below it and a `default` value. The default is what the form starts with, so the form never saves a value the module would not use by itself.

| Type | Field Created |
|------|---------------|
| `boolean` | Checkbox |
| `checkboxes` | Group of checkboxes, one per entry in `options` |
| `radio-button` | Radio button group, one per entry in `options` |
| `select` | Drop-down list of `options`; may carry `presets` (see below) |
| `combobox` | Drop-down list of suggested `options` that also accepts free text |
| `number` | Number input field |
| `text-area` | Multi-line text area |
| `date` | Date picker |
| `color` | Color picker |
| `code-area` | Markdown editor |
| Default (`string`) | Single-line text input field |

    --{{1}}--
A `select` field can define `presets`: for each option, the values to fill into sibling fields of the same configuration type.
An entry is either a plain value, or an object with `value` and `options` that also narrows the suggestions of a `combobox`.
Picking an option overwrites these fields, even if they were edited by hand.

      {{1}}
```json
{
  "stationConfig": {
    "workflow": {
      "type": "select",
      "options": ["arduino-avr", "micropython"],
      "hint": "Pick a board family to fill in the fields below",
      "presets": {
        "arduino-avr": {
          "board": {
            "value": "arduino:avr:uno",
            "options": ["arduino:avr:uno", "arduino:avr:mega"]
          },
          "port": "/dev/ttyACM0",
          "baud": 9600
        },
        "micropython": {
          "port": "auto",
          "baud": 115200
        }
      }
    },
    "board": { "type": "combobox", "options": ["arduino:avr:uno", "esp32:esp32:esp32"] },
    "port": { "type": "string" },
    "baud": { "type": "number", "default": 9600 }
  }
}
```


### YAML-Modules

    --{{0}}--
To simplify the development of small modules, a module can also be declared in a single YAML file instead of an HTML page.
Edrys fetches the file and builds the HTML page from it.
A URL is treated as a YAML module if it ends in `.yml` or `.yaml`.

    --{{1}}--
The keys mirror the meta tags of an HTML module. With `load` you list the scripts and stylesheets to include, `style` holds the CSS, `body` the HTML of the page, and `main` the JavaScript that runs in it.

      {{1}}
``` yaml
name: Hello Edrys                      # module name (like <title>)
description: Greets everyone in the room. See <a href="https://github.com/edrys-labs">edrys-labs</a>
icon: mdi-hand-wave                    # optional, a Material Design icon name
show-in:                               # optional, a list; default is '*'
  - lobby
  - Room *

module-config: |-                      # optional, same schema as the meta tag, as a string
  {
    "config": {
      "greeting": { "type": "string", "default": "Hello" }
    }
  }

load:
  scripts:                             # loaded in this order
    - https://edrys-labs.github.io/module/edrys.js
    - lib/helpers.js                   # relative to the YAML file
  links:
    - https://edrys-labs.github.io/module/vendor/water.min.css

style: |-
  body { padding: 1rem; }

body: |-
  <h1 id="greeting">Loading…</h1>

main: |-
  Edrys.onReady(() => {
    const greeting = Edrys.module.config?.greeting || "Hello"
    document.getElementById("greeting").textContent =
      `${greeting}, ${Edrys.liveUser?.displayName}!`
  })
```

    --{{2}}--
A complete real-world example is the Markdown-It module, which is available both as an HTML page and as a YAML file.

      {{2}}
<section>

- https://github.com/edrys-labs/module-markdown-it/blob/main/module.yaml

**Good to know**

- Absolute URLs in `load` are included as normal `<script>` and `<link>` tags. Relative ones are resolved against the URL of the YAML file, fetched, and then added to the page.
- Like modules with the `fetch` meta tag, YAML modules are inlined: they run on a `data:` URL with an opaque origin. The browser's `localStorage` is not available there, and therefore neither are `Edrys.setItem` and `Edrys.getItem`. Use `Edrys.getState` to keep state.
- The `description` is shown as text with links, like that of an HTML module (see [Metadata](#Metadata)).

</section>
