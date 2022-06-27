## Things I want to know more about

* Get started
- This means that the server can push messages to clients. Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients.

* Introduction
Writing a chat application with popular web applications stacks like LAMP (PHP) has normally been very hard. It involves polling the server for changes, keeping track of timestamps, and it’s a lot slower than it should be.

- Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server.

* The web framework
- The first goal is to set up a simple HTML webpage that serves out a form and a list of messages. We’re going to use the Node.JS web framework express to this end. Make sure Node.JS is installed.

- First let’s create a package.json manifest file that describes our project. I recommend you place it in a dedicated empty directory (I’ll call mine chat-example).
---
{
  "name": "socket-chat-example",
  "version": "0.0.1",
  "description": "my first socket.io app",
  "dependencies": {}
}
---
* Now, in order to easily populate the dependencies property with the things we need, we’ll use npm install:

--- 
npm install express@4
---
* Once it's installed we can create an index.js file that will set up our application.
---
const express = require('express');
const app = express();
const http = require('http');
const server = http.createServer(app);

app.get('/', (req, res) => {
  res.send('<h1>Hello world</h1>');
});

server.listen(3000, () => {
  console.log('listening on *:3000');
});
---
- This means that:

- initializes app to be a function handler that you can supply to an HTTP server (as seen in line 4).
-We define a route handler / that gets called when we hit our website home.
- We make the http server listen on port 3000.
- If you run node index.js you should see the following:

- A console saying that the server has started listening on port 3000 And if you point your browser to http://localhost:3000:

- A browser displaying a big 'Hello World'
- Serving HTML
- So far in index.js we’re calling res.send and passing it a string of HTML. Our code would look very confusing if we just placed our entire application’s HTML there, so instead we're going to create a index.html file and serve that instead.

- Let’s refactor our route handler to use sendFile instead.
---
app.get('/', (req, res) => {
  res.sendFile(__dirname + '/index.html');
});
---
- Put the following in your index.html file:
----
<!DOCTYPE html>
<html>
  <head>
    <title>Socket.IO chat</title>
    <style>
      body { margin: 0; padding-bottom: 3rem; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; }

      #form { background: rgba(0, 0, 0, 0.15); padding: 0.25rem; position: fixed; bottom: 0; left: 0; right: 0; display: flex; height: 3rem; box-sizing: border-box; backdrop-filter: blur(10px); }
      #input { border: none; padding: 0 1rem; flex-grow: 1; border-radius: 2rem; margin: 0.25rem; }
      #input:focus { outline: none; }
      #form > button { background: #333; border: none; padding: 0 1rem; margin: 0.25rem; border-radius: 3px; outline: none; color: #fff; }

      #messages { list-style-type: none; margin: 0; padding: 0; }
      #messages > li { padding: 0.5rem 1rem; }
      #messages > li:nth-child(odd) { background: #efefef; }
    </style>
  </head>
  <body>
    <ul id="messages"></ul>
    <form id="form" action="">
      <input id="input" autocomplete="off" /><button>Send</button>
    </form>
  </body>
 </html>
---

If you restart the process (by hitting Control+C and running node index.js again) and refresh the page it should look like this:

A browser displaying an input and a 'Send' button
Integrating Socket.IO
Socket.IO is composed of two parts:

A server that integrates with (or mounts on) the Node.JS HTTP Server socket.io
A client library that loads on the browser side socket.io-client
During development, socket.io serves the client automatically for us, as we’ll see, so for now we only have to install one module:

npm install socket.io
That will install the module and add the dependency to package.json. Now let’s edit index.js to add it:

const express = require('express');
const app = express();
const http = require('http');
const server = http.createServer(app);
const { Server } = require("socket.io");
const io = new Server(server);

app.get('/', (req, res) => {
  res.sendFile(__dirname + '/index.html');
});

io.on('connection', (socket) => {
  console.log('a user connected');
});

server.listen(3000, () => {
  console.log('listening on *:3000');
});
Notice that I initialize a new instance of socket.io by passing the server (the HTTP server) object. Then I listen on the connection event for incoming sockets and log it to the console.

Now in index.html add the following snippet before the </body> (end body tag):

<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io();
</script>
That’s all it takes to load the socket.io-client, which exposes an io global (and the endpoint GET /socket.io/socket.io.js), and then connect.

If you would like to use the local version of the client-side JS file, you can find it at node_modules/socket.io/client-dist/socket.io.js.

Notice that I’m not specifying any URL when I call io(), since it defaults to trying to connect to the host that serves the page.

If you now restart the process (by hitting Control+C and running node index.js again) and then refresh the webpage you should see the console print “a user connected”.

Try opening several tabs, and you’ll see several messages.

A console displaying several messages, indicating that some users have connected
Each socket also fires a special disconnect event:

io.on('connection', (socket) => {
  console.log('a user connected');
  socket.on('disconnect', () => {
    console.log('user disconnected');
  });
});
Then if you refresh a tab several times you can see it in action.

A console displaying several messages, indicating that some users have connected and disconnected
Emitting events
The main idea behind Socket.IO is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.

Let’s make it so that when the user types in a message, the server gets it as a chat message event. The script section in index.html should now look as follows:

<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io();

  var form = document.getElementById('form');
  var input = document.getElementById('input');

  form.addEventListener('submit', function(e) {
    e.preventDefault();
    if (input.value) {
      socket.emit('chat message', input.value);
      input.value = '';
    }
  });
</script>
And in index.js we print out the chat message event:

io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    console.log('message: ' + msg);
  });
});
The result should be like the following video:

Broadcasting
The next goal is for us to emit the event from the server to the rest of the users.

In order to send an event to everyone, Socket.IO gives us the io.emit() method.

io.emit('some event', { someProperty: 'some value', otherProperty: 'other value' }); // This will emit the event to all connected sockets
If you want to send a message to everyone except for a certain emitting socket, we have the broadcast flag for emitting from that socket:

io.on('connection', (socket) => {
  socket.broadcast.emit('hi');
});
In this case, for the sake of simplicity we’ll send the message to everyone, including the sender.

io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    io.emit('chat message', msg);
  });
});
And on the client side when we capture a chat message event we’ll include it in the page. The total client-side JavaScript code now amounts to:

<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io();

  var messages = document.getElementById('messages');
  var form = document.getElementById('form');
  var input = document.getElementById('input');

  form.addEventListener('submit', function(e) {
    e.preventDefault();
    if (input.value) {
      socket.emit('chat message', input.value);
      input.value = '';
    }
  });

  socket.on('chat message', function(msg) {
    var item = document.createElement('li');
    item.textContent = msg;
    messages.appendChild(item);
    window.scrollTo(0, document.body.scrollHeight);
  });
</script>


# Rooms
A room is an arbitrary channel that sockets can join and leave. It can be used to broadcast events to a subset of clients:

* Joining and leaving
You can call join to subscribe the socket to a given channel:

io.on("connection", (socket) => {
  socket.join("some room");
});
And then simply use to or in (they are the same) when broadcasting or emitting:

io.to("some room").emit("some event");
You can emit to several rooms at the same time:

io.to("room1").to("room2").to("room3").emit("some event");
In that case, a union is performed: every socket that is at least in one of the rooms will get the event once (even if the socket is in two or more rooms).

You can also broadcast to a room from a given socket:

io.on("connection", (socket) => {
  socket.to("some room").emit("some event");
});
In that case, every socket in the room excluding the sender will get the event.

* To leave a channel you call leave in the same fashion as join.

* Default room
Each Socket in Socket.IO is identified by a random, unguessable, unique identifier Socket#id. For your convenience, each socket automatically joins a room identified by its own id.

This makes it easy to implement private messages:
---
io.on("connection", (socket) => {
  socket.on("private message", (anotherSocketId, msg) => {
    socket.to(anotherSocketId).emit("private message", socket.id, msg);
  });
});
---

* Sample use cases
broadcast data to each device / tab of a given user
---
io.on("connection", async (socket) => {
  const userId = await fetchUserId(socket);

  socket.join(userId);

  // and then later
  io.to(userId).emit("hi");
});
---
 - send notifications about a given entity
---
io.on("connection", async (socket) => {
  const projects = await fetchProjects(socket);

  projects.forEach(project => socket.join("project:" + project.id));

  // and then later
  io.to("project:4321").emit("project updated");
});
---

* Disconnection
- Upon disconnection, sockets leave all the channels they were part of automatically, and no special teardown is needed on your part.

- You can fetch the rooms the Socket was in by listening to the disconnecting event:
---
io.on("connection", socket => {
  socket.on("disconnecting", () => {
    console.log(socket.rooms); // the Set contains at least the socket ID
  });

  socket.on("disconnect", () => {
    // socket.rooms.size === 0
  });
});
----

* Room events
Starting with socket.io@3.1.0, the underlying Adapter will emit the following events:

create-room (argument: room)
delete-room (argument: room)
join-room (argument: room, id)
leave-room (argument: room, id)
 
 Example:
---
io.of("/").adapter.on("create-room", (room) => {
  console.log(`room ${room} was created`);
});

io.of("/").adapter.on("join-room", (room, id) => {
  console.log(`socket ${id} has joined room ${room}`);
});
---

[Socket.io Chat Example](https://socket.io/get-started/chat/)
[Rooms](https://socket.io/docs/v4/rooms)
[Namespaces](https://socket.io/docs/v4/namespaces/)