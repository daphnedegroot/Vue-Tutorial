# Vue.js

## Listening to Events

Lets dive into a new project.

Create a new HTML and JS file and copy the content down below into the corrensponding file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script scr="vue.js"></script>
</head>
<body>
    <div id="app">
        <button>Click me</button>
        <p>{{ counter }}</p>
    </div>
    <script src="main.js"></script>
</body>
</html>
```

```javascript
new Vue({
    el: '#app',
    data: {
        counter: 0
    }
});
```
I want to hook up this button that when I click on it, it increases this counter. Well we already saw how to hook this button up but now we understand a bit better what happened back then.

```html
<button v-on:>Click me</button>
```

I'm using another directive, ``v-on`` and if ``v-bind`` allows us to bind something in our template, to pass data to it, then ``v-on`` is kind of the opposite, we bind to something or better said we listen to something to receive something from our template. 

And what do I want to receive here? Well, an event. So ``v-on`` also takes an argument and the argument is the name of the event we want to consume or we want to listen to.

So let's say the event here is click and you're not limited to click, you can use any dom event existing for the button, this would include mouse enter, mouse leave, whatever default dom events are on a button, you then pass as an argument or on the other side of the equal sign between the quotation marks, the function or the code you want to execute when clicking on this button.

```html
<button v-on:click="increase">Click me</button>
```

Now let's hook it up to a function, I'll name it increase and I'll add it down here where I'll add my methods block and then the increase function where I obviously want to access the counter and increase the value by 1. 

```javascript
new Vue({
  el: '#app',
  data: {
    counter: 0
  }, methods: {
  	increase: function(){
    	this.counter++;
    }
  }
});
```

If I now hit control and click this button, you see it increase there, so that was pretty easy I guess. Now let's dive deeper into events and learn more about them.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/dscbtL0j/).

[Next -->](./Getting-Event-Data.md)