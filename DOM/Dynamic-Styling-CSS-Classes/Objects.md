# Vue.js

## Dynamic Styling with CSS Classes - Using Objects

So we saw how we could attach and detach css classes conditionally.

What if you don't want to store this object here in your html template code? It's very simple here but imagine we would also have this blue class here for the blue css class and set this to the opposite of attachRed.

```html
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="{red: attachRed, blue: !attachRed}"></div>
  <div class="demo" :class="{red: attachRed}"></div>
  <div class="demo"></div>
</div>
```

If I now save this, you see you can toggle between blue and red here but now this object grows rather big. Well I could go down to my vue instance and create a new computed property for that since it will depend on my attach red property it needs to be computed. 

So here I could call this div classes and this of course is a function as all computed properties, which should return me a javascript object namely the object I set up here. 

```JS
new Vue({
  el: '#app',
  data:{
  	attachRed: false
  },
  computed: {
  	divClasses: function(){
    	return{
      	red: attachRed,
        blue: !attachRed
      }
    }
  }
});
```

So in here I will simply have ``red``, ``attach red`` and then ``blue`` which is the ``opposite``. Now that of course won't work because keep in mind here in our vue.js code, in the javascript code, we have to access the properties with ``this`` at the beginning.

```JS
new Vue({
  el: '#app',
  data:{
  	attachRed: false
  },
  computed: {
  	divClasses: function(){
    	return{
      	red: this.attachRed,
        blue: !this.attachRed
      }
    }
  }
});
```

Now with that change in place, I can simply replace my object here with div classes and if I save this, you see the same behavior as before but now outsourced in a property, in this case a computed property. 

```HTML
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="divClasses"></div>
  <div class="demo" :class="{red: attachRed}"></div>
  <div class="demo"></div>
</div>
```

If you wouldn't have this dependency of course, you wouldn't need to use a computed property and our template is much leaner again due to this being stored in our javascript code now.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/1s9z6otp/).

[Next -->](./Names.md)