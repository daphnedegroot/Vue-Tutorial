# Vue.js

## Saving Time with Shorthands



Well so over the last lectures, we learned a lot about outputting data, listening to events, transforming data, dynamically recalculating properties with computed properties, watching our properties and much more. All the time we used syntax like this, v-on for events and v-bind for binding to attributes of our elements here, like the ref element. Now if you use that and you're going to use this a lot, there is a shortcut, a short a way of writing this. 

Take a look at this example:

```Html
<div id="app">
  <button v-on:click="changeLink">Click to change link</button>
  <a v-bind:href="link">Link</a>
</div>
```

```Javascript
new Vue({
  el: '#app',
  data: {
    link: 'http://www.google.com'
  },
 methods: {
 	changeLink: function(){
  	this.link = 'http://www.apple.com';
  }
 }
});
```

For events, you can replace v-on and the colon with an @ sign, vuejs will recognize this and behind the scenes, rendered it or treat it as v-on colon but with @ click, we're basically saying at the click event, do the following, so it's the same as v-on and then colon, just a shorter way of writing it.

And for v-bind, we get a similar shortcut, we can remove v-bind and just use colon ref, so the code now is exactly the same as before but a bit shorter and for the rest of course, I will use the shorter code as there is nothing wrong with it and why not save some characters especially since I believe this syntax is very readable as well.

```HTML
<div id="app">
  <button @click="changeLink">Click to change link</button>
  <a :href="link">Link</a>
</div>
```

So that's just something to be aware of.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/qbak95rw/).

[Next -->](./Assignment-3.md)