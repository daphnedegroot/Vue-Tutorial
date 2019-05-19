# Vue.js

## Writing JavaScript Code in the Templates
Before concluding these lectures on outputting data with the interpolation or before the bind and listening to events, there's one important thing I need you to know or I need you to be aware of.

Right now, we're most of the time using this in a way that once we output something, we output a single property like for the counter or x and y, before we saw though that we also could call a function which
worked fine, that is by the way how we mostly use it for events, here we simply pass the reference to a function, to a method we want to execute.

Be aware that in all the places where you can access your vue instance,
so when listening to a click event or when outputting the counter, so whatever we access our vue instance, you can write any valid javascript code as long as it's only is one expression and doesn't contain an if or in statement or a for loop or something like that.

So simple javascript statements can be evaluated, so for example, I could duplicate my click button and i don't want to call increase but I directly want to increment the counter by one.

```html
<div id="app">
  <button v-on:click="increase(2, $event)">Click me</button>
  <button v-on:click="counter++">Click me</button>
  <p>{{ counter }}</p>
  <p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span v-on:mousemove.stop="">DEAD SPOT</span>
  </p>
  <input type="text" v-on:keyup.enter="alertMe">
</div>
```

Well I can simply call counter++ here and if I save this, you see now I can click this button just fine and it increments my counter. The same is true here for the string interpolation, I could easily output counter times two, 

```html
<div id="app">
  <button v-on:click="increase(2, $event)">Click me</button>
  <button v-on:click="counter++">Click me</button>
  <p>{{ counter * 2 }}</p>
  <p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span v-on:mousemove.stop="">DEAD SPOT</span>
  </p>
  <input type="text" v-on:keyup.enter="alertMe">
</div>
```

after saving, you see that now I can increment by two here even though I normally would only increment by one and here where I do increment by two, well it's by four now.

So this is perfectly valid, you could even write short ternary expressions here like for example check if this is greater than 10, in which case you could say greater than 10 otherwise you could say smaller than 10. 

```html
<div id="app">
  <button v-on:click="increase(2, $event)">Click me</button>
  <button v-on:click="counter++">Click me</button>
  <p>{{ counter * 2 > 10 ? 'Greater then 10' : 'Smaller then 10' }}</p>
  <p v-on:mousemove="updateCoordinates">
    Coordinates: {{ x }} / {{ y }}
    <span v-on:mousemove.stop="">DEAD SPOT</span>
  </p>
  <input type="text" v-on:keyup.enter="alertMe">
</div>
```


If you now hit save, you see that it is smaller than 10 until I obviously seem to pass the 10 border. This is how you can work with the templates here, it really is a mixture of html and javascript code as long as you use template expressions like the double curly braces here and this gives you this very strong connection between your html code, your template and your javascript code, your vue instance, all managed automatically by vuejs and giving you thus the power to write very, well powerful and user friendly applications where you have this natural connection.

Think about the effort, code like this would take to write with jQuery especially once you introduce more complex relations and need to do all this checking for possible changes in onepart of your application on your own. 

Speaking of that, we'll dive deeper into the reactivity of our properties in the next few lectures.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/fezrxvh2/).

[Next -->](./Two-Way-Binding.md)