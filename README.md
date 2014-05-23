# Android Developer Interview

## Summary

Mockup an android app which can talk to WebSocket backend.

The background of the challenge is to achieve realtime data synchronization bewteen the app and backend, e.g UI update when data changes.

## Environment

To save your time setting up the test environment. We've prepared a preconfigured online server as well as a simple debug client

* Client: http://threepin.test.letsface.com
* Server: http://socket-io-faker.test.letsface.com

In your app, you may connect to the online server or setup one locally from [socket-io-faker](https://github.com/letsface/socket-io-faker). And play it with [ThreePin](https://github.com/letsface/ThreePin) to get familiar with its behaviour.

### fake server

The fake server will respond to following operation.

1. version: setup the api version
2. login: login to the system
3. create: create new guest
4. find: find a list of existing guests
5. logout: logout the system

It will also publish an update on guest status every 10 seconds

Please note that

1. 'login' is allowed only after setting up the api 'version'
2. 'create' and 'find' are allowed only after 'login'
3. after 'logout', 'create' and 'find' will not be allowed

### to do

Create an android app which can

1. configure the server url and port
2. connect to the server
3. enter username and password
4. login to the system (emit version then login)
5. fetch the guest list and display their name and attended states
6. update attended state when receiving message from server

### message format

All messages are emit and listened on event 'api'. The content of the message is as following

```
{
  "op": "version",
  "payload": "v1"
},
```

See [sample messages](https://github.com/letsface/ThreePin/blob/master/threepin.json) for more.

The server will respond in following format

```
{
  "op": "out",
  "payload": {
    "version": "v1",
    "methods": ["create", "currentUser", "find", "findOne", "login",
      "logout", "remove", "sync", "update", "version"
    ]
  }
}
```

See [answering rules](https://github.com/letsface/socket-io-faker/blob/master/test/fixtures/rules.json) of the fake server for details.

## Note

* On the fake server, only `op` name is checked, but you should encapsulate necessary data, pretending to talk to a real server.
* Please focus on the **communication** part rather than UI.

## Links that may help

* [Socket.IO](http://socket.io/)
* [AndroidAsync](http://koush.com/AndroidAsync)
* [Socket.IO java client](https://github.com/Gottox/socket.io-java-client)
* [Connecting to a Socket.IO server from Android](http://nkzawa.tumblr.com/post/46850605422/connecting-to-a-socket-io-server-from-android)
