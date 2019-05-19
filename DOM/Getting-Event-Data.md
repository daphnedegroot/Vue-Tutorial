# Vue.js

## Getting Event Data from the Event Object

A important thing about events is the default event object we can listen to.

There is this event object created by the javascript or by the dom which holds some information, for example on a click event that holds the coordinates of where this click event happened.

Now let's say we want to access this information because we might be interested in outputting the data, so I'll quickly add a new paragraph in the html where I will say coordinates and I want to output the coordinates here, so that will output the x coordinate and then let's say next to it, it will output a y coordinate.

```html
<div id="app">
  <button v-on:click="increase">Click me</button>
  <p>{{ counter }}</p>
  <p>Coordinates: {{ x }} / {{ y }}</p>
</div>
```

Now of course these two don't exist so quick so I'll quickly set them up here, X and Y, and then upon hovering over this paragraph,

```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    x: 0,
    y: 0,
  }, methods: {
  	increase: function(){
    	this.counter++;
    }
  }
});
```

I want to update these two values. So inside the p element I can say we ``v-on:mousemove`` and execute update coordinates. 

```html
<p v-on:mousemove="updateCoordinates">Coordinates: {{ x }} / {{ y }}</p>
```

Well let me quickly write this method down in the script, update coordinates and now I would need access to the coordinates, I would need access to this ``event`` object which gets created automatically. 

```Javascript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    x: 0,
    y: 0,
  }, methods: {
  	increase: function(){
    	this.counter++;
    },
    updateCoordinates: function(){
    
    }
  }
});
```

Turns out it not only gets created automatically by the dom or by javascript, it also gets passed automatically to each function we execute through this vuejs ``v-on`` binding, vue.js does this for us. So now I can conveniently execute event.

```javascript
updateCoordinates: function(event){
    this.x = event.clientX;
    this.y = event.clientY;
}
```

So I can conveniently pass ``event`` inside the function parameters and then inside the function, I can say ``this.x`` equals event, ``clientX`` as it turns out to be and ``this.y`` event ``clientY``, ``clientX`` and ``clientY`` are the default properties names of the ``event`` object, has nothing to do with vue.js, and I also rename this to update coordinates as I call it up.

You now see once I hover over it, these coordinates here update. This is a how we can listen to something else than a click but b very importantly, it shows us how we can pass this event object which again is created automatically and use it as we do here.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/ugko2w3b/).

[Next -->](./Arguments-with-Events.md)