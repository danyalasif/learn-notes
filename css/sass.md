---
title: "SASS"
metaTitle: "SASS | DevNotes"
metaDescription: "A SASS land"
---


## [Learn Sass In 20 Minutes | Sass Crash Course](https://www.youtube.com/watch?v=Zz6eOVaaelI)

* SASS uses `.scss` extension
* Use `Live Sass Compiler` in VS Code to compile SASS easily

### Variables
* Variables help in keeping things consistent around the CSS
	* Store the site colors in one place so there's less duplication thus lower chance of fuck ups
	* 
* Create a variable like `$primaryBtn: red` and this can be used anywhere in the scss file 

### Nesting
* Nesting is a powerful part of SASS
```
header {
	button {
		&:hover {}
	}
	p {}
}
```
* Nesting keeps the code organized  and in one place
* To add after, hover kind of properties use the `&` symbol

### Partials
* Partials are a way to organize code in parts 
* Sass supports partials  and lets you import these in one main file
* e.g.
``` 
_header.scss
_variables.scss
```
And can be imported in the main file as such
``` @import "./header";```

### Mixins
* Mixins are like functions which can be defined once and reused everywhere
```
@mixin varName($parameter) {
	display: flex;
	justify-content: $parameter
}

header {
	@include varName(center);
}

button {
	@include varName(left);
}
```

### Inheritance
* Inheritance helps with reusability of the already defined styles
```
@import "./header";

.contact {
	@extend header;
	//This has now all styles of header
	//Defining further styles will overwrite the styles of header
}
```

### Calculations
Sass supports basic calculations, addition, subtraction, division etc.
``` width: 100% - 20%```


