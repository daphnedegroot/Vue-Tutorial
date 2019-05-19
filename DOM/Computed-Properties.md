# Vue.js

## Reacting to Changes with Computed Properties
Let's come back to the reactivity I was talking about earlier.

For this we need another new project:

HTML:
```HTML
<div id="app">
  <button v-on:click="increase">Increase</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result }}</p>
</div>
```

JavaScript:
```Javascript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    result: '',
  },
  methods: {
  	increase: function(){
    	this.counter++;
        this.result = this.counter > 5 ? 'Greater 5' : 'Smaller 5';
    }
  }
});
```

Until now, we had rather simple examples, we clicked a button, we changed one property, we kind of touched on that if we wanted to output some text depending on another property. Remember that counter where I said greater than 10 and smaller than 10? Well I kind of rebuilt the example here, this time I'm not outputting the text or I'm not outputting this code here, where I check if it is greater than 5 here in my template in the string interpolation though I could do that but I outsourced it here.

This leads to the following behavior, if I click here, we see smaller than 5 at the beginning but once we go over 5, it changes to greater than 5 or greater 5. 

That is nice and that's easy to maintain for this simple application. Now imagine that the counter variable would be used in a lot of different places, a lot of other properties would depend on the counter here, it could quickly get problematic to manage them all in this increased function or think you would have another place where you set this counter, then you would need to keep both in sync and well, that is really hard to maintain, it would already get harder to maintain if I were to add the decrease button here, execute the decrease method and simply duplicate the increase method here to now also have the decrease method.

```HTML
<div id="app">
  <button v-on:click="increase">Increase</button>
  <button v-on:click="decrease">Decrease</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result }}</p>
</div>
```

```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    result: '',
  },
  methods: {
  	increase: function(){
    	this.counter++;
      this.result = this.counter > 5 ? 'Greater 5' : 'Smaller 5'
    },
    decrease: function(){
    	this.counter--;
      this.result = this.counter > 5 ? 'Greater 5' : 'Smaller 5'
    }
  }
});
```

And I do the same check as before again, so here I can go over 5 and then back to smaller. This works but you notice that I have this code in two places and if I would have other source of setting the counter, it would quickly get unmaintainable. Thankfully, vuejs makes it much easier than that to model such cross property dependencies.

I'll get rid of both the functions here, I'll get rid of the whole methods object and I'll rewrite the code to simply increase the counter here and decrease it here.

```HTML
<div id="app">
  <button v-on:click="counter++">Increase</button>
  <button v-on:click="counter--">Decrease</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result }}</p>
</div>
```

```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    result: '',
  }
});
```

Now how do I update my result now? I can't set the logic here, data is not reactive so I can't say ``this.counter > 5 ?`` and then execute my code here, this will not work, that is not how the data property works but turns out we do have a way to still do that.

The first one would be one we already saw in action, if I reintroduce my methods I could add a result method here and all I could do here would be I can simply return this statement from before where I simply check if this counter is greater than 5 in which case I could say greater 5 and otherwise say smaller than 5, whatever text you want output.

```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
  },
  methods: {
      result(){
          return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
      }
  }
});
```

```HTML
<div id="app">
  <button v-on:click="counter++">Increase</button>
  <button v-on:click="counter--">Decrease</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result() }}</p>
</div>
```


I could then call result here, get rid of this result property and upon re-rendering this, you would see it now works again. This is one way of doing it, now we already improved this a lot because now we don't have to worry about the different sources influencing our counter.

It still has a disadvantage though. 

If I add a third button here where I do something totally different, let's say I have my ``secondCounter`` which I ``increment``, so increment would increase second and then I'll add it here. 
```HTML
<div id="app">
  <button v-on:click="counter++">Increase</button>
  <button v-on:click="counter--">Decrease</button>
  <button v-on:click="secondCounter++">Increase Second</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result() }}</p>
</div>
```


```JavaScript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    secondCounter: 0
  },
  methods: {
      result(){
          return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
      }
  }
});
```


If I have such a set up, this result method here will still get executed on upon each updating of the page, vuejs will update the page whenever it finds the need to do so which will be whenever one of its data properties changes, we obviously since we output them here need to update the page and it doesn't know if the result function we execute here does use one of the properties we changed.

So it doesn't know if the change of second counter influences the result method and therefore it re-executes this method as well.
This might not be a problem for this rather lightweight function here but imagine you have a function which takes longer to run, which runs more complicated code and which you don't want to re-execute even though it is not needed to be re-executed. 

For this case, we got a new property on our global, and our view instance here, it's called ``computed`` and it also takes a javascript object, just like data and methods. 

```Javascript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    secondCounter: 0
  },
  computed:{
    output: function(){
        return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
    }
  },
  methods: {
    result: function(){
        return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
    }
  }
});
```

The computed property or object here also allows us to store properties for example output do not reuse result but here, it is not directly the data instead this also is a function where we return the value this property here should eventually have so I can copy the code from down there.

It looks like the result method here, it just has a different name but actually we use it differently. I can output both here, let's say so I'll use string interpolation again and I'll use output like this, notice the difference, no parentheses.

```html
<div id="app">
  <button v-on:click="counter++">Increase</button>
  <button v-on:click="counter--">Decrease</button>
  <button v-on:click="secondcounter++">Increase Second</button>
  <p>Counter: {{ counter }}</p>
  <p>Result: {{ result() }} | {{ output }}</p>
</div>
```

I don't call that as a function, I use it like a property, like property stored in my data object, it isn't stored there but I can use it in just the same way. And that's important to keep in mind, everything stored in computed can be used just like you use a property in the data object. 

The interesting thing about it is, for this if I save that, we see smaller than 5 twice and we see that both updates just fine, the difference behind the scenes is the ``result`` function gets called every time because vuejs doesn't know if it needs to re-run this, it doesn't know if we use any property in this function which was changed.

For computed properties, it does analyze the code and it is aware of this, so for a computed property it is aware that output is not interested in the second counter at all and thus will not be run if I hit to increase second button and I can prove this to you. 

```Javascript
new Vue({
  el: '#app',
  data: {
    counter: 0,
    secondCounter: 0
  },
  computed:{
    output: function(){
    	console.log('computed');
      return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
    }
  },
  methods: {
    result: function(){
    	console.log('Methods');
      return this.counter > 5 ? 'Greater then 5' : 'Smaller then 5' ;
    }
  }
});
```

```html
<p>Counter: {{ counter }} | {{ secondCounter }}</p>
```

Let's simply add a console log where I would say computed here in the case of my computed function and for the normal method here, I will say method. I can go to my counter and simply output my second counter as well and if I now hit save and open up my console, watch what happens.

I'm going to hit increase first, we see method and computed, so both get executed here which makes sense because I changed my counter and my output, my computed property here depends on this counter, so it makes sense that it gets recalculated because again, it depends on it.

The result method gets executed anyways as I explained and I can prove this. Watch what happens if I hit increase second, keep in mind this only increases the second counter, something which is not used in my computed output property here, thus if I hit it, we only see method being added, computed is not getting executed, so this function ``output`` is not getting executed at all, only this function ``result`` because again, it gets executed all the time because vue.js is not aware of what's inside of it.

It is of my computed property though which is why we don't see computed when clicking increase second. This is how we can use and how we should use computed properties if we get dependencies like this, it is the best way to do it because we're caching the result, we're not unnecessarily recalculating it if there is no need to recalculate.

So only use the function way here ``result()``  if you know that you don't want to cache the result, that you want to recalculate every time the dom gets updated because for some reason, you know that this is required even though you might update a property which is not used in this function you're calling here at all. 

There might be such cases but most of the time it probably isn't the case so make sure to really take advantage of this great concept of computed properties here.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/g54mj2fs/).

[Next -->](./Alternative-Computed-Properties.md)