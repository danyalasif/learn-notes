---
title: "Flutter Input"
metaTitle: "Flutter Input | DevNotes"
metaDescription: "Flutter Input | DevNotes"
---

`TextField`

```dart
TextField(
    keyboardType: TextInputType.numer | email,
    style: Theme.of(context).textTheme.display1,
    decoration: InputDecoration(
        labelText: "input",
        errorText: _showValidationError ? "Invalid Number" : null
    )
)
```

3 Ways to retrieve the text

* onChanged - as soon as user types anything
* onSubmitted - when user presses the enter or submit button
* controller - Implements a listener


