# Vue.js

## Accessing Data in the Vue Instance

This is especially important to keep in mind because in our vue instance, if we here wanted to output the title in this function so we don't want to return hello but we want to return a title, 

```Javascript
new Vue({
    el: '#app',
    data: {
        title: 'Hello World'
    },
    methods: {
        sayHello: function() {
            return title;
        }
    }
});
```

then this will not work because unlike in the template where we do have direct access to all these properties and methods, vuejs proxies them for us, here in the javascript code, that does not work.

But we still have an easy access, you notice that the title property sits on an object which is called data and normally we wouldn't be able to access it by calling this title because this would not refer to the data object.


```Javascript
new Vue({
    el: '#app',
    data: {
        title: 'Hello World'
    },
    methods: {
        sayHello: function() {
            return this.title; // This doesnt work here
        }
    }
});
```

Thankfully vue.js also provides us some magic here, it proxies these properties and the same is by the way true for the method so it would also work that we call a method like this. It proxies them in a way that by simply calling this anywhere in our vue instance object, will give us access to these proxy properties, methods, whatever it is, so we can call this title to access the title in the data field because behind the scenes and I will come back to this in the vuejs instance module in this course, behind the scenes, vuejs kind of creates an easy access for us to these properties.

That is the important thing to keep in mind here and especially keep in mind, there is a difference inside a template, were we don't need to use the keyword this, altho inside the javascript, we do. Well and with this change in place, if I update it again we see hello world again but this time by calling a function which now accesses our title property.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/mo7ckq96/).

[Next -->](./Binding-Attributes.md)