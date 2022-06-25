## Things I want to know more about

# Socket.io

* WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011. 


* Web Socket Request/Response Handshake
- To establish a WebSocket connection, the client sends a WebSocket handshake request, for which the server returns a WebSocket handshake response.

*  (Links to an external site.)Key features of Socket.IO
It helps in broadcasting to multiple sockets at a time.
It works on all platform, server or device, ensuring equality, reliability, and speed.
It automatically upgrades the requirement to WebSocket
It requires both libraries Client side as well as a server-side library.
These are some reserved events on the server-side socket object:

Connect
Message
Disconnect
Reconnect
Ping
Join
Leave
Also there is reserved events on the client-side socket object:

Connect
Connect_error
Connect_timeout
Reconnect, etc.

* Once the socket is created, we should listen to events on it. There are totally 4 events:

open – connection established,
message – data received,
error – websocket error,
close – connection closed.

let socket = new WebSocket("ws://javascript.info"); 
And if we’d like to send something, then socket.send(data) will do that.

let socket = new WebSocket("wss://javascript.info/article/websocket/demo/hello");

socket.onopen = function(e) {
  alert("[open] Connection established");
  alert("Sending to server");
  socket.send("My name is John");
};

socket.onmessage = function(event) {
  alert(`[message] Data received from server: ${event.data}`);
};

socket.onclose = function(event) {
  if (event.wasClean) {
    alert(`[close] Connection closed cleanly, code=${event.code} reason=${event.reason}`);
  } else {
    // e.g. server process killed or network down
    // event.code is usually 1006 in this case
    alert('[close] Connection died');
  }
};

socket.onerror = function(error) {
  alert(`[error] ${error.message}`);
};