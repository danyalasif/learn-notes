---
title: "Vue Methods"
metaTitle: "Vue Methods | DevNotes"
metaDescription: "Vue Methods"
---

We can attach methods to objects by adding a `methods` object

So,

```vue
new Vue({
    el: '#app',
    data() {
        return {
            counter: 0,
            x: 0
        }
    },
    methods: {
        increment() {
            this.counter++; //this refers to current object
        },
        decrement() {
            this.counter--; 
        }
    }
})
```

and in the HTML, it would be used like:

```html
<div id="app">
    <button @click="increment">+</button>
    <span> {{ counter }} </span>
    <button @click="decrement">-</button>
</div>
```



Computed properties will be cached after they are computed