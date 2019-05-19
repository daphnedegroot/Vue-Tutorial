# Vue.js

## Setting Styles Dynamically (without CSS Classes)

```HTML
<div id="app">
  <div class="demo"></div>
  <div class="demo"></div>
  <div class="demo"></div>
  <hr>
  <input type="text" v-model="color">
</div>
```

```CSS
.demo {
  display: inline-block;
  width: 100px;
  height: 100px;
  margin: 10px;
  background-color: gray;
}

.red {
  background-color: red;
}

.green {
  background-color: green;
}

.blue {
  background-color: blue;
}
```

```JS
new Vue({
  el: '#app',
  data:{
    color: 'green'
  }
});
```

For this next part, i got the same setup as before, my three boxes and also already the input field which is bound to this color property with two way data binding. Now I showed you how to use classes, css classes, how to attach and detach them and how to select them both either by having key value pairs with name and condition or just the name of the class.

Here I want to show you how you can directly interact with the styles attached to an element so you don't have to use classes necessarily,
let's say you only want to change the style and let's say you want to change the color, well then it is as easy as binding to style and then as a javascript object, the key is the style you want to bind to, background color.

```html
<div id="app">
  <div class="demo" :style="{'background-color': color}"></div>
  <div class="demo"></div>
  <div class="demo"></div>
  <hr>
  <input type="text" v-model="color">
</div>
```

Now note, this will not work, you have to enclose it either in single quotation marks because the dash is not a valid character in a property name or remove the single quotation marks, remove the dash and use camel case syntax, background Color, like this.

```html
<div id="app">
  <div class="demo" :style="{backgroundColor: color}"></div>
  <div class="demo"></div>
  <div class="demo"></div>
  <hr>
  <input type="text" v-model="color">
</div>
```

With that, the value then is color, this property. If I now save this, I can change this to green and you see I can now set it directly like this and of course again, the source of this value doesn't matter, I use an input here because it's easiest for us to add it but it could also be the end result of an asynchronous task, of a calculation, whatever. As before, you don't have to pass the object like this, you could also set up your style object here.

```JS
new Vue({
  el: '#app',
  data:{
    color: 'green'
  },
  computed: {
  	myStyle: function(){
    	return {
      	backgroundColor: this.color,
      }
    }
  }
});
```

So again since I want to use this color, I'll set up a computed property and I'll name it my style which will be a function as all computed properties are, where I return an object since I expect an object in my style binding. Here I will set backgroundColor, camel case important, bind this to this color. 

```HTML
<div id="app">
  <div class="demo" :style="{backgroundColor: color}"></div>
  <div class="demo"></div>
  <div class="demo"></div>
  <hr>
  <input type="text" v-model="color">
  <input type="text" v-model="width">
</div>
```

And I also want to be able to input the width, so let copy the inputfield and I'll also bind to width, let's add this new property to our Javascript, set it to 100 initially and then here, I will easily set this by setting the width to and now this width plus pixels, to convert it into a pixel value which is needed for the style. 

```Javascript
new Vue({
  el: '#app',
  data:{
    color: 'green',
    width: 100,
  },
  computed: {
  	myStyle: function(){
    	return {
      	backgroundColor: this.color,
        width: this.width + 'px',
      }
    }
  }
});
```

```html
<div id="app">
  <div class="demo" :style="{backgroundColor: color}"></div>
  <div class="demo" :style="myStyle"></div>
  <div class="demo"></div>
  <hr>
  <input type="text" v-model="color">
  <input type="text" v-model="width">
</div>
```

With that I can now refer to this new object to set style equal to my style to this computed property and if I save this, you see I can now change the width of this second block as well as the color as I set it up as a computed property here just because it's depending on other properties and I set it as a new object which allows me to directly bind to this object here.

So that is really the same as it work with classes but here focused on individual styles and I think it's easy to imagine how easy you could create a progress bar by dynamically adjusting the width as we do here.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/vbz5ma0L/).

[Next -->](./Styles-Array.md)