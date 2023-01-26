---
title: "Expo"
metaTitle: "Expo | DevNotes"
metaDescription: "Expo | DevNotes"
---

Expo is a complex wrapper around react-native which handles many complex tasks that need to be handled manually otherwise. It's a pretty nifty tool that can be used to quickly set up a react native application and then used to quickly deploy to android or iphone stores. 

It also allows for continuous deployments, so anyone in the world can scan a code with the expo app and use it just like that!

### Pros

* Allows rapid development and setup, requires much less time to see something than native react-native development setup
* Abstracts away a lot of pain points that could potentially slow down development
* Build tools give the flexibility to deploy on both Android and iOS (without needing Apple devices)


### Cons

* Potentially limiting for large projects, anything more than a beginner project would be hindered by the limitations of expo and eventually you'd have to eject out of it -- Ejecting has its own overhead but is great if you started from expo
* The abstractions of expo may be too much and hide away too much of the necessary complexity that a person needs to get acquainted with
* There are hard limitations on what expo can achieve, many of the advanced features like WebRTC, Push Notifications via third party services, etc. are not available in expo