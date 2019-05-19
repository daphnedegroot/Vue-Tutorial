# Vue.js

## Disable Re-Rendering with v-once

Let's enhance this little application a little more. 
Let's say we have a title, h1 title and here I will output title, remember this is just hello world. 

```html
<div id="app">
  <h1>{{ title }}</h1>
  <p>{{ sayHello() }} - <a v-bind:href="link">Google</a></p>  
</div>
```

In say hello I will obviously do the same even though I call a function, now in this function, let's say I will set this title equal to just hello like this:

```Javascript
new Vue({
  el: '#app',
  data: {
    title: 'Hello World!',
    link: 'http://www.google.com',
  },
  methods: {
    sayHello: function() {
    	this.title = 'Hello!';
      return this.title;
    }
  }
});
```

If I now hit refresh, well we see hello twice obviously because when we execute say hello, we're overwriting the value of title, we're setting it to just hello, so we're outputting hello in both places.

Now what if in the title, we wanted to stick to the first initial value title we had and don't want to change this if it changes later in our code like it does here? We can do this! 

There is another directive vuejs ships with which we can attach to an html element which holds an interpolation like this one which is called ``v-once``. By adding this to an element, all the content inside of this element will only be rendered once, it will not be updated if it changes later on, like here where we change it in a later place.

```html
<h1 v-once>{{ title }}</h1>
```

If I now hit refresh you see hello world because it keeps the initial value, it doesn't adjust once it is overridden. You may have examples in your application where you want this behavior and ``v-once`` then makes it very easy to stick to the initial value and not use any other values this property might take at a later point of time.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/wrve2ofp/).

[Next -->](./Raw-HTML.md)