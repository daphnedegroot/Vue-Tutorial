# Vue.js

## Modifying an Event - with Event Modifiers

When working with events, there are a couple of things you`ll oftentimes encounter in real applications which you need to solve and as you learned, vue.js makes solving these things easier. But what do you what are these things? 

Let's enhance our application here by taking this paragraph where we output the coordinates and I want to create kind of a dead spot, so here I'll enter a ``span`` and once I hover over this, I don't want to update the coordinates.

```html
<p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span>DEAD SPOT</span>
</p>
```

Now of course right now, if I save this it is still updated because this ``span`` is part of this paragraph on which I'm listening to any mouse moves. 

```html
<p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span v-on:mousemove="dummy">DEAD SPOT</span>
  </p>
```

I can now set up my own event and I will call it mouse move as well and here I simply want to execute nothing, well one solution would be to still execute a function here, so I'll name it ``dummy`` and add it down here in the methods object.

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
    dummy: function(event){
    	event.stopPropagation();
    }
  }
});
```

``Dummy`` of course would be a ``function`` and in this function, all I want to do is I want to fetch the ``event`` which gets passed automatically and here I could call ``stopPropagation()`` to make sure that it does not propagate up to elements holding this element, this span here.

If I now hit save, you'll see that once I hover over to that spot, the coordinates no longer get well updated because now we're stopping the propagation which means only handle the element here in this handler, don't let it propagate up to any elements which might hold this element.

Yeah we could do it like this but we can even get a bit easier than that, I can remove the dummy function and Inside the ``span`` i can simply execute nothing but use a so-called modifier, an event modifier,
it allows me to modify the behavior of this event, that's where the name comes from, clever huh. 

I add such a modifier by adding a dot after the name of the event which I pass as an argument to be on and the modifier I want to use here is stop for stop propagation.

```html
<span v-on:mousemove.stop="">DEAD SPOT</span>
```

If I now hit save, we see the same behavior as before even though I don't even execute a function here because vuejs now does this for me, it kind of has this internediate function which is between my function, no function in this case and this time when the event is emitted or when we get the event. It then runs this little function which simply does one thing, it stops the propagation of the event.

We also get other modifiers, the probably most important second one being ``prevent`` for running ``prevent.default``, so running stop propagation with the ``stop`` modifier and ``prevent.default``, the two common methods you have when working with the ``default event object``, these are available with these modifiers like ``.stop``.

You can also chain them just as a side note by adding ``.prevent`` as well which won't do anything here but you could add them or chain them, just like that.

### Resources
Take a look at the official documentations about Event Modifiers.
- [Event Modifiers: Official Documentation](https://vuejs.org/v2/guide/events.html#Event-Modifiers) 

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/2wfs6har/).

[Next -->](./Keyboard-Events.md)