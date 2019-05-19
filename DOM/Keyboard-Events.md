# Vue.js

## Listening to Keyboard Events

We saw event modifiers in the last lesson, we not only have event modifiers we also have key modifiers. To demonstrate them, let me add an input field here. 

```html
<div id="app">
  <button v-on:click="increase(2, $event)">Click me</button>
  <p>{{ counter }}</p>
  <p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span v-on:mousemove.stop="">DEAD SPOT</span>
  </p>
  <input type="text" v-on:keyup="alertMe">
</div>
```

In this input field, I want to listen to the key up event which obviously is fired whenever the user releases the key and the key goes up. Here what I want to do is I want to throw an alert, so I'll call this alert me here and then down there in the methods property, I'll add the alert me function. So this shall get executed whenever we type something into this input field and here I simply want to throw an alert which says alert.

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
		},
    alertMe: function(){
    	alert('Alert!');
    }
  }
});
```

Now this will probably get very spammy, I save this and I type here and yeah I get alerts, not really the best user experience. Maybe I only want to send an alert if I submit this, so if I hit enter let's say. We can add a key modifier for this, so like before with .stop for the event modifier, a key modifier is also added by adding dot and then the name of the key, for example enter. 

```html
 <input type="text" v-on:keyup.enter="alertMe">
```

You will find inside the Resources chapter a list of available modifiers or where to find out which modifiers exist, .enter exists, you would also have .tap, .esc, you can also chain them for example by typing .space.

And now if I hit save and start typing, we don't see anything but I hit save, we saw the alert, I hit enter, we see an another alert. 

This is how we can add our own key modifiers. This enables us to only listen to specific keys but of course, these modifiers are only available for key related events like key up here, which makes sense I guess.

### Resources
Take a look at the official documentations about Key Modifiers.
- [Key Modifiers: Official Documentation](https://vuejs.org/v2/guide/events.html#Key-Modifiers) 

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/npz6vmqb/).

[Next -->](./Assignment-2.md)