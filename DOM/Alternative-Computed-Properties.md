# Vue.js

## An Alternative to Computed Properties: Watching for Changes

When working with dependencies, vuejs also has another way of doing this. 

We're using a computed property right now, I can also use yet another property on the vuejs instance, the ``watch object``, so that's another new object we're learning about right now. 

In computed, we set up the property and then as a function, we set up the logic how this property should be computed, for ``watch``, it kind of **works the other way around**. 

Here as a key, I set up the property name I want to watch, for example counter, so this has to match one of my properties, in this case the data property counter here.

Then as a function, I specify the code I want to execute whenever the counter changes and I pass or vuejs automatically passes the value of this upcoming change to this function. This allows me to react to changes and therefore here, I could also set a global output variable if I would have that and if it wasn't computed as it is here and set this up the other way around, which certainly will work though I will tell you right away that **it is a best practice to use computed properties wherever you can**, simply because they are **more optimized** due to this caching and so on, it really allows vuejs to run more optimal, to avoid unnecessary tasks.

Though there are cases where you need to react to every change, also there is another case where computed properties **won't do the trick** and that is if you need **asynchronous tasks** to be run. 

Computed properties always need to run synchronously which means you're returning something here and that needs to happen as soon as possible or immediately, there is no way you can reach out to a server or do some other asynchronous task in between. If you need to run such a task or as I just mentioned before, you need to run some other code which really is triggered when a property updates and which is not solved by a computed property, then ``watch`` is for you.

So here we might simply want to reset the counter after let's say two seconds, so I'll add a timeout here and I'll say that after two seconds, I want to execute this first function here. 

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
  watch: {
  	counter: function(value){
    	var vm = this;
    	setTimeout(function(){
      	
      },2000);
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

Now important, since this is now a closure in this callback here, I have to store in my view instance in a separate variable so this which allows me to conveniently access my properties and so on needs to be stored in a variable because while it is available with this, all throughout in my default vuejs objects and functions here, this is not the case for a callback closure like this one here. In here, I can then call vm, but now again just like before, access counter and set it to 0 to reset it after two seconds.

```JavaScript
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
  watch: {
  	counter: function(value){
    	var vm = this;
    	setTimeout(function(){
      	vm.counter = 0;
      },2000);
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

With this in place, if I now save, I'll rapidly increase the counter and we see it go back to 0 after two seconds because we had watch in place which will be called whenever the counter changes, thus executing this code and as you see here, able of executing asynchronous task.

The reason for this of course is that inside the function I'm not returning anything, here I'm not resetting a property which needs to be recalculated, here I'm simply specifying some code which should be run whenever some  property we set up here as a key changes, in this case, the counter.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/xz73jqr2/).

[Next -->](./Shorthands.md)