---
title: "Flutter Navigation"
metaTitle: "Flutter Navigation | DevNotes"
metaDescription: "Flutter Navigation | DevNotes"
---

## Navigation Widgets

Navigation is done through a navigation widget too. It handles to and fro movment and naviation. 

We can pass context between routes. Navigator can push and pop screens to navigation from one screen to other.

`InkWell` widghet has a `onTap` method which can be used to move from one area to another
```dart
void _navigateToPlace(BuildContext context) {
    if(Navigator.of(context).canPop()) {
        Navigator.of(context).pop();
    }

    Navigator.of(context).push(MaterialPageRoute<Null>(
        builder: (BuildContext context) {
            return Scaffold(  //Returns another screen or widget, this can easily be another premade screen like AboutScreen()
                appBar: AppBar(
                    elevation: 1.0,
                    title: Text(
                        name,
                        style: Theme.of(context), textTheme.display1,
                    ),
                    centerTitle: true,
                    backgroundcolor: color[100],
                ),
                body: ConverterRoute(
                    name: name,
                    units: units,
                    color: color
                ),
                resizetoAvoidBottomPadding: false
            );
        }
    ));
}

```

