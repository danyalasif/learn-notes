---
title: "Object-Oriented Programming"
metaTitle: "OOP | DevNotes"
metaDescription: "OOP | DevNotes"
---


## Objects
Objects allows us to store functions with their associated data.

### Object Literal way
```javascript 
const user1 = {
	name: "Dan",
	score: "100",
	increment: function() {
		user1.score++;
	}
	//Can easily add more functionality
	decrement: function() {
		user1.score--;
	}
}
```

### Dot Notation
```javascript
const user2 = {};
user2.name = "Dog"
user2.score = 5;
user2.increment = function () {user2.score++;};
```
### Object.create -- Bad Approach
```javascript
const user3 = Object.create(null)

user3.name = "Dog2"
user3.score = 9;
user3.increment = function() {user3.score++;};
```

### Generating Objects using functions
* Defining functions inside of a object creator would lead to extreme unoptimizations as each instantiation would contain the functions.
* Prototype chain is a better way of doing this. If you want to add an increment function to every instance of user.

### Object.create -- Better Approach 
```javascript
function userCreator (name, score {
	const newUser = Object.create(userFunctionScore);
	newUser.name = name;
	newUser.score = score;
	return newUser;
}

const userFunctionStore = {
	increment: function() {this.score++;},
	login: function() {console.log("You're loggedin");}
}

const user1 = userCreator("Phil", 4);
const user2 = userCreator("Dog", 5);

user1.increment();
```

* As soon as you declare new user with Object.create, it returns an empty object but with hidden properties which referrence to any function that's been passed in the Object.create paramaters.
* If JS does not find the property in an object it goes and look up in the ```__proto__``` hidden property.

### The new & this keywords -- Functions & Objects
* ```new ``` keyword automates creating the user object and returning the user object. So we don't need to do Object.create or return
* Function defined with the ```function``` keyword are a function-object combo and can act as an object. If you use dot notation ,you can access its object bits. It does not overwrite or lose access to the function bits.
* functions contain the ```prototype``` property which itself is an object to replace our ```__proto__``` in objects
* The ```new``` keyword does the following:
	* Bind ```this: { }``` to any objecy
	* Calls the ```__proto__``` binding on the objec
	* returns the object