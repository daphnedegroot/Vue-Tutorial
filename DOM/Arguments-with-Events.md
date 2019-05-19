# Vue.js

## Modifying an Event - with Event Modifiers
What if we wanted to pass our own argument? For example when increasing the counter, we're currently incrementing it by one, what if we wanted to pass our own step by which it should get incremented? Nothing easier than that, when calling increase or setting up this reference, I can also add parentheses and pass my own argument, for example two. 

```html
<button v-on:click="increase(2)">Click me</button>
```

Now with this, I say or I want to say that I want to increase this counter by two, since I've pass it as an argument here, I can go down there to my method and in the increase function, I simply listen to step or add the argument of the function.

```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    x: 0,
    y: 0,
  }, methods: {
  	increase: function(step){
    	this.counter += step;
    },
    updateCoordinates: function(event){
        this.x = event.clientX;
    	this.y = event.clientY;
    }
  }
});
```

I can then say ``this.counter += step`` to now increase it by this step instead of one. So if I save this, you're now see I click and it increases by two all the time, this is how easy I can pass my own argument. And finally what if I not only wanted to pass my own argument but both my own argument and this automatically created event object? That's also very simple, I can simply add a second argument and now here the naming is important.

```html
<button v-on:click="increase(2, $event)">Click me</button>
```

Vuejs automatically fetches this default event argument and stores it in a kind of a variable we can access here named ``$event``. So this is a protected name, don't override it and make sure to not get it wrong.

Doing it this way, I can now also fetch this event inside the function and I could use it in my increase method if I wanted to too conveniently well use both my own argument and the automatically created and now also passed event object future vuejs gives us access to.

```Javascript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    x: 0,
    y: 0,
  }, methods: {
  	increase: function(step, event){
        this.counter += step;
    },
    updateCoordinates: function(event){
        this.x = event.clientX;
    	this.y = event.clientY;
    }
  }
});
```

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/1769kav0/).

[Next -->](./Event-Modifiers.md)