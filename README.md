## Socket Server for Live Chat

A Simple script to join/left user and send messages to all connected users.

Please refer for more about [Socket](https://www.npmjs.com/package/ngx-socket-io)
### How to run server

* Clone project to your local machine
```
git clone http://192.168.1.73:6768/mital/chat-socket-server.git
```

* Install node packages
```
npm install
```
* Run server on your localhost
```
npm run start
```

### How to use into your Application
*For socket connection you must Connect with [Socket](https://www.npmjs.com/package/ngx-socket-io)*
 
* Add New User
```javascript
    const name = `user-${new Date().getTime()}`;
    socket.emit('set-name', name);
```

* Get User Join/Left Status
```javascript
    socket.fromEvent('user-changed').subscribe(data => {
      const user = data.user;
      if (data.event === 'left') {
        console.log('User left : ' + user);
      } else {
        console.log('User joined : ' + user);
      }
    });
```

* Send New Message
```javascript
    socket.emit('send-message', { text: 'Message' });
```

* Receive New Message
```javascript
    socket.fromEvent('message').subscribe(message => {
      console.log('Message received : ', message);
    });
```
