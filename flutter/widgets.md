---
title: "Flutter Widgets"
metaTitle: "Flutter Widgets | DevNotes"
metaDescription: "Flutter Widgets | DevNotes"
---

Widhget are the foundation of flutter apps, A widghet is a description of part of a user interface.

[Flutter Widget Index](https://flutter.dev/docs/reference/widgets)

In flutter everything is a widget, there are two types of widgets specifically,
* Stateful
* Stateless


## Stateful Widgets
These widgets store and manipulate the state of a widget throughout the lifecycle of a widget. When a widget state is changed, it's rerendered in the next frame

## Stateless Widgets
Stateless widgets are immutable, meaning, they only render at runtime what is passed to them as parameters/properties and changing these properties don't trigger a render. They are built with what is given to them on start.