# Vue.js

## Dynamic Styling with CSS Classes - Basics

Still with me? 

You are now really the kings of outputting data and listening to events. With that, we got a lot of things covered, you will use a lot in your day to day applications, listening to user input and outputting transform data or whatever data really is a core task you'll well have in all your applications and which really makes up most of your applications, at least when it comes to this frontend connection, so to rendering it in the browser.

But there is one other piece you will also use a lot and that is changing the styling, attaching css classes. Look at this example.

HTML:
```html
<div id="app">
  <div class="demo"></div>
  <div class="demo"></div>
  <div class="demo"></div>
</div>
```

CSS:
```CSS
.demo{
    display: inline-block;
    
    width: 100px;
    height: 100px;
    margin: 10px;
    
    background-color: gray;
}
```

JavaScript:
```JS
new Vue({
  el: '#app'
});
```

I got three divs here which are gray blocks by default because I set up this demo css class, no vue.js code involved here at all, yes I have setup this element connection but I'm not doing anything there as you can clearly tell. 

Now it would be interesting to see how we can attach classes to these divs. So let's quickly create three new css classes, a red class which will set the background color to you guessed it, red and then copying this class, a green class which does the same with well surprisingly green and then the blue class which does the same with blue, so now we get three new css classes here which we can use in our application.

CSS:
```css
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

Now of course I could attach it like that but that would be pretty boring right, let's instead see what vuejs can do for us, let's start simple and say I want to attach this red block only if I click on this element and detach it if I click again. 

To be able to well show this, I'll add my data property to the view instance which is hooked up to this code which has this as a template and here, I will set up a new property, I'll name it attach red and initially I'll set it to false, to say no I don't want to attach it initially.

```JS
new Vue({
  el: '#app',
  data:{
  	attachRed: false
  }
});
```

Upon clicking on it, I want to set attach red to well what it currently is not, so to the opposite, with this exclamation mark, I'm basically switching it from true to false and the other way around.

```HTML
<div id="app">
  <div class="demo" @click="attachRed = !attachRed"></div>
  <div class="demo"></div>
  <div class="demo"></div>
</div>
```

In order to conditionally attach a css class, I need to bind to the class property here and I can do this with colon class, notice that it doesn't matter that I alredy attach class here with the demo, with colon class. I'm using vuejs syntax and I'm not reusing the class attribute here. Yes I'm binding to it but behind the scenes, vuejs will merge this all into one class object.

```html
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class=""></div>
  <div class="demo"></div>
  <div class="demo"></div>
</div>
```

So here, I need to pass a javascript object as an argument, this is just what vuejs expects here and this object should be which css class has a key, should I attach and has a value, should I attach it or not,
so true or false.

Now here I clearly want to attach the red css class, you could also enclose it in single quotation marks and you would need to do this if your class contains a special character like a dash but since it doesn't here, I don't have to and then the condition will be attach red which is false initially but could be true. 

```HTML
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="{red: attachRed}"></div>
  <div class="demo"></div>
  <div class="demo"></div>
</div>
```

If I now hit save, you see I can now turn on and off this red class here due to this single code, this single line of code here where I set up my red class as a key here referring to this css property and connect it to attach red which is true or false and switch constantly by clicking on this div.

```HTML
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="{red: attachRed}"></div>
  <div class="demo" :class="{red: attachRed}"></div>
  <div class="demo"></div>
</div>
```

Of course I could now copy that and also add it to another div and if I now save this, now both are of course switched on and off because they share the same property, attach red which is the one well deciding on whether it should be attached or not.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/1wtn7r63/).

[Next -->](./Objects.md)