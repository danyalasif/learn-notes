---
title: "SignalR"
metaTitle: "SignalR | DevNotes"
metaDescription: "SignalR | DevNotes"
---

SignalR is a WebSockets implementation for dotnet applications. I used the frontend client for this which was @aspnet/signalr, this version is for dotnet core 2.0 and the version for 3.0 is @microsoft/signalr

## Basics

* Building a connection first, can pass multiple different params to it for logging and other features

```javascript
let connection = new SignalR.HubConnectionBuilder()
    .withUrl('https://api.forcespenpals.net/signalhub', {
      accessTokenFactory: () => token
    })
    .configureLogging(SignalR.LogLevel.Debug)
    .build()
```

* Starting the connection

```javascript
    connection
      .start()
      .then(() => {
        console.log('SignalR: STARTED!@!#!@#!@#!')
        setInterval((): void => {
          if (connection.state) {
            connection.invoke('heartbeat')
            console.log('HeartBeat')
          }
        }, 15000)
      })
      .catch(err => console.log('Error while establishing connection :(', err))
```


* Listening to events sent from server
SignalR uses the `on` method to listen to methods coming from server and `off` method to close the connection
```
connection.on('messageReceived', (data: any) => {
    console.log(data);        
})

connection.off('messageReceived', c => {
    console.log('messageRecieved Off', c)
})
```

* Sending events to server
SignalR uses the `invoke` method to call methods on the server,

A simple way to keep the server alive is sending a heartbeat
```
connection.invoke('heartbeat')
```
Wrapping this in an interval and calling it constantly would do the trick (code above in starting a connection)

|| Note: in the 3.0 version a simple `.withAutomaticReconnect()` can be passed in the `HubConnectionBuilder()` chain and it would do. -- [Ref](https://www.jerriepelser.com/blog/automatic-reconnects-signalr/)

* Callback if connection closes

For running any processes and logging errors if the connection drops, there's a `onclose` method

```javascript
connection.onclose((error: any) => {
    console.log('Connection closed', JSON.stringify(error))
})
```


### Referrences

* https://docs.microsoft.com/en-us/aspnet/signalr/overview/guide-to-the-api/handling-connection-lifetime-events#signalrvstransport
* https://www.jerriepelser.com/blog/automatic-reconnects-signalr/
* https://docs.microsoft.com/en-us/javascript/api/@aspnet/signalr/hubconnection?view=signalr-js-latest#on
* https://docs.microsoft.com/en-us/aspnet/core/signalr/configuration?view=aspnetcore-3.0&tabs=dotnet
* https://docs.microsoft.com/en-us/aspnet/core/signalr/introduction?view=aspnetcore-3.0