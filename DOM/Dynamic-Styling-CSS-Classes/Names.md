# Vue.js

## Dynamic Styling with CSS Classes - Using Names
   
Sometimes you don't want to decide if a certain class should be attached or not but you want to calculate or dynamically derive which class should be attached or not.

Let's say we add a horizontal line and then a user input, I'll bind it to my color property:

```JS
new Vue({
  el: '#app',
  data:{
  	attachRed: false,
    color: 'green'
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

initially I'll set color to green, referring to this green css class as I will use it on my last remaining unstyled div where I want to set up class. And now what? Now here, I simply will set this equal to color.

```HTML
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="divClasses"></div>
  <div class="demo" :class="{red: attachRed}"></div>
  <div class="demo" :class="color"></div>
  <hr>
  <input type="text" v-model="color">
</div>
```

So now, this is connected to the color property here and the color property is set through this input field. If I now save this, we see the green class here and we see green in the input field. 

With that said I can go down to the input field, delete it, you see the green class disappearing and I can change it to blue or to red, whatever css class I have set up.

Now what's happening here? I'm not determining if the green class should be attached or not with true or false, instead I'm directly outputting a class name here and this class name happens to be stored in this color property which is settable through the input, it could be set through anything, doesn't have to be set through input, the key thing here is that I'm storing the value and not if or not, but instead what should be attached, the class name.

You can also attach multiple classes by using the array syntax, now this syntax down here will still work as you can see but now I could also add this condition here, this object as a second argument, now I get a mixture.

```HTML
<div id="app">
  <div 
    class="demo" 
    @click="attachRed = !attachRed" 
    :class="divClasses"></div>
  <div class="demo" :class="{red: attachRed}"></div>
  <div class="demo" :class="[color, {red: attachRed}]"></div>
  <hr>
  <input type="text" v-model="color">
</div>
```

I now always have my green class here since I wrote green here, now it's blue and now it's red but if I switch this back to blue and now I click on the first div and remove blue here, you now see it's red because now it also has this red class attached to it because I'm now setting up an array of classes which I want vuejs to analyze and then merge it all into one list of css classes based on whatever these items in the array resolves to and what do they resolve to? 

They resolve to this color property which is a css class and to an object, if it's an object, then vue.js knows okay, it's a key value pair where the key is css class and the value is the condition if this class should be attached or not, here attached red is the property deciding whether to attach class or not.

So we get both syntaxes using the css class directly or using an object where then the key is the css class and the value is the condition. This is important to keep in mind because it gives you a lot of flexibility, you see how much flexibility we got here.
We got so many different ways of calculating our classes and attaching them, that really is amazing and should give you all the tools you need in your application to get the desired result.


## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/8ef7hxsz/).

[Next -->](./../Styles-Dynamically.md)