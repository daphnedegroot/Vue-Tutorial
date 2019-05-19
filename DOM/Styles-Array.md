# Vue.js

## Styling Elements with the Array Syntax

Now as before, you can also combined is by here on the last div creating an array where I for one set my style. But now let's say I also pass as a second element a new object where I set the height equal to the width plus pixels.

```html
<div id="app">
  <div class="demo" :style="{backgroundColor: color}"></div>
  <div class="demo" :style="myStyle"></div>
  <div class="demo" :style="[myStyle, {height: width + 'px'}]"></div>
  <hr>
  <input type="text" v-model="color">
  <input type="text" v-model="width">
</div>
```

so even though it's called width, I can of course also use this value to set the height to create a square again. So now if I save this and I enter 50 into the input, you see that the third block now also changed in both width and height because I'm setting up both my style which sets color and the width and this extra object which sets the height. 

This is how you can use styles and classes and bind directly to both classes and styles using the different syntaxes to pass the styles and classes you want to pass.

One important note, if you use styles binding like this, vuejs will automatically prefix your styles to work in all browsers supporting vuejs in the first place.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/e45tx37L/).

[Next -->](./Assignment-4.md)