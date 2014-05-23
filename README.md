# Android Developer Interview

## Summary

Mockup an android app which can talk to WebSocket backend.

The purpose of using WebSocket is to achieve realtime data synchronization bewteen the app and backend, e.g UI update when data changes.

## Challenge

In this challenge, the app will talk to a fake socket-io server

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

See [sample messages](https://github.com/letsface/ThreePin/blob/master/threepin.json)

Please focus on the **communication** part rather than UI.

## Links that may help

* [Socket.IO](http://socket.io/)
* [Socket.IO java client](https://github.com/Gottox/socket.io-java-client)
* [Connecting to a Socket.IO server from Android](http://nkzawa.tumblr.com/post/46850605422/connecting-to-a-socket-io-server-from-android)
