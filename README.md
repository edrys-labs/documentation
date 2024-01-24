# edrys-Lite Documentation

Welcome to the Edrys documentation!

- 📖 Use the contents below to get started
- 💬 For questions and discussions, please visit our
  [Gitter community](https://gitter.im/edrys-org/community)
- 🐞 For bug reports and feature requests, visit the
  [issues tab](https://github.com/edrys-labs/edrys-lite/issues)

## Contents

1. [Lab-Creation](#Lab-Creation)
2. [Developing Modules](#Developing-Modules)
3. [Working with Stations](#Working-with-Stations)

## Lab Creation

## Developing Modules

Edrys labs are based on the concept of "modules".
A module is a classroom/lab building block.
You can create your own modules or explore existing modules and add them to your classroom.

A module is just an HTML page that is run in an iframe and shown to your students, teachers, and on stations.
You can make the module behave differently depending on where it is currently loaded.
Modules use the Edrys.js API to send and receive messages in real time, allowing you to build any live functionality without setting up any real-time infrastructure, authenticating users, or configuring anything else, as that is all handled upstream by Edrys.

### Usage

To use a module you simply host it anywhere and paste its link into the Edrys-Lite app.

- To explore existing ready-to-use modules, check out the
  [`edrys-lite` tag on GitHub](https://github.com/topics/edrys-lite)
- The easiest way to start developing modules is to use the
  [Official Module Template](https://github.com/edrys-labs/module)
 - Bring your own stack by using Edrys.js:
 
 ```html
 <script src="https://edrys-labs.github.io/edrys-lite/module/edrys.js"></script>
 ```

## The API

When using Edrys.js, you have to listen for the onReady event that will be
called when the module has been fully loaded:

```js
Edrys.onReady(() => console.log("Module is loaded!"));
```

There is also the onUpdate event, which is called on any real-time state changes:

```js
Edrys.onUpdate(() => console.log("Something has changed in the class"));
```
### Metadata

Edrys scrapes module HTML files for metadata. It looks at meta tags in your HTML
and stores this information. The following meta tags can be set:

- `description`:
  module description that will be shown to people adding your module.
  The description can consist of HTML with links and base configuration examples as well.
- `show-in`:
  defines where the module will be shown.
  Can be "*" to load it everywhere, "chat" for the Lobby and other chat-rooms, or "station" to load it only on Stations
- Page title: the page title tag will be used as the module name

For an example of how to use meta tags, check out the
[tags in the template module](https://github.com/edrys-labs/module-reference/blob/main/index.html).

### Config

Users of the module can pass in some run-time configuration to your module to customize its behavior.
The content and structure of this config is entirely up to you. You can read the config in this manner:

```js
console.log(Edrys.module.config); // Always available
console.log(Edrys.module.studentConfig); // Only available when this module is loaded to a student
console.log(Edrys.module.teacherConfig); // Only available when this module is loaded to a teacher
console.log(Edrys.module.stationConfig); // Only available when this module is loaded on a station
```

To get where the module is currently loaded:

```js
console.log(Edrys.role); // Is one of "teacher", "student", or "station"
```

### Messaging

Modules can send and receive messages delivered with an at-most-once guarantee.
Messages are transferred in real time to everyone else in the same room.
Messages each have a "subject" and a "body" which you can use however you want
(eg. Use subject for message type and body as stringified JSON).

To send a message:

```js
Edrys.sendMessage("subject", "body");
```

To receive messages:

```js
Edrys.onMessage(({ from, subject, body }) => {
  console.log("Got new message: ", from, subject, body)
});
```

Messages are scoped to the module, meaning you won't get messages from other modules.
This prevents creating ugly dependencies across modules.
However, if necessary, "promiscuous mode" can be used to listen to all messages in the room regardless of module:

```js
Edrys.onMessage(
  ({ from, subject, body, module }) => {
    console.log("Got new message: ", from, subject, body, module) 
  }, promiscuous=true);
```

### Live Class Reactive API

Edrys modules receive lots of data which can be useful in developing extra functionality into Edrys.
This can be found in `Edrys.liveClass`, which is reactive in real-time, meaning if you make any changes to that object (for
example set a student's room to something else), it will be applied in real time to everyone in the class!
Provided of course you have proper permissions, modules loaded on the student's end won't be able to make use of this API.

For example, the [Auto-Assign Module](https://github.com/edrys-org/module-auto-assign) uses this API to automatically move students around rooms at a configurable interval.

### Persistent State

Messages are ephemeral (eg. newly joining students won't see previously sent messages, so request-reponse semantics are usually employed).
For more persistent state, you can for example use the S3 API and store data there at a known location.
A more integrated solution will be available in the future.

## Working with Stations

Edrys Stations are a feature that allows building remote labs, automated grading, and other experiences that require a non-human teacher at the other
end. 

A station is simply an Edrys class open in the browser in "station mode" and left to respond to student queries.
This functionality is handled by the modules loaded on the station end.
Stations can run on any machine  with a browser on it (eg. a server, laptop, Raspberry Pi, or even an always-on old
smartphone).

To create a station, navigate to class settings and copy the special class station URL.
You can now open this URL on any browser (you will have to log in with a teacher's account).
When you navigate back to your class, you will see a special room has been added, represeting that station.
Click on the room to talk to the station, or drag students into the room to get them to use the station.
When you close the station URL, that room will disappear on its own.

To make the concept clearer, here is what an Edrys class looks like with stations:

<div align="center">
<img src="stations/structure.png" style="width: 60%" />
</div>

## Example Arduino Remote Lab

An example use case of stations is to create a remote Arduino Lab, where students can remotely interact with an Arduino (upload code to it and see the result through a camera) that is physically hosted somewhere else (eg. university grounds).
In this example, a university would like to allow its students access to their fleet of lab devices remotely, removing any need for students to be physically present to experiement with the devices. 

To achieve this with Edrys, each Arduino would be connected to a computer with internet access (in this example a Raspberry Pi), and a station would be open on the each computer's browser.
We can use a USB webcam with the [Station-Stream](https://github.com/edrys-org/module-video-chat) module to let students see the Arduino, and the [Code Editor](https://github.com/edrys-org/module-code) module to allow students to upload code to it. The overall setup for one station could look like this:

<div align="center">
<img src="stations/arduino-lab.png" style="width: 70%"/>
</div>

Something to note in this setup is the presece of the Arduino Comms Agent (more info [here](https://github.com/edrys-org/module-code#usage)), which is a simple localhost server that allows modules in the browser to talk to the Arduino (since the browser can't natively do that, unlike with the webcam).

Overall, this allows easy set up of remote labs without configuring security, servers, port forwarding, or any other infrastructure. All that is needed is a browser running, which can be repeated for any number of stations. This produces a portable, scalable, and easy-to-share setup that can be replicated even by non-technical teachers. The same principles apply to any other lab devices (since modules can be reused, combined, or developed to accomodate any setup).

## Auto-Assign

A common use case when building remote labs or automated grading is the need for students to be automatically assigned to stations without human intervention (in this case, a teacher dragging students in and out of station rooms). The official [Auto-Assign Module](https://github.com/edrys-org/module-auto-assign) allows adding such functionality.

