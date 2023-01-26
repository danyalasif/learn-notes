---
title: "Push Notifications"
metaTitle: "Push Notifications | DevNotes"
metaDescription: "Push Notifications | DevNotes"
---

Push Notifications are an easy task in Expo but the documentations is either outdated or misleading a bit.

For setting up PN for android, you must set it up with Firebase service FCM (Firebase Cloud Messaging) and integrate it with your application. 

The steps are as follow:

* Make a new project on firebase (The project name should be the same as the expo app)
* download the googleservice.json file and put it at root of your app
* Referrence the file in app.json at `android/googleservice`



### Referrence

* https://console.firebase.google.com/
* https://snack.expo.io/r1Agp6GjH?platform=ios (IMPORTANT!)
* https://expo.io/dashboard/notifications
* https://docs.expo.io/versions/latest/guides/push-notifications/#2-call-expos-push-api-with-the
* https://docs.expo.io/versions/latest/workflow/configuration/