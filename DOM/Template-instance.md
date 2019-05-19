# Vue.js

## How the VueJS Template Syntax and Instance Work Together

So we saw how we can output a single property stored in the data field of our vue instance and this is important, data stored in the vue instance, in the data property for example, the title here can be output in our template just like that.

```html
<p>{{ title }}</p>
```

We don't need to write ``this.title``, we don't need to write ``data.title``, we have access to all the properties in the data object just like that. And that's really important to keep in mind, of course this makes outputting it very easy as we don't have to manually access our Vue instance or save it in a variable which we then would access, no, all of that happens behind the scenes for us, we can access all properties in the data object just like that.

Not only in the data object though, if we reintroduce the methods key which we already saw in the first module of this course, where we can store some methods of this vuejs instance, then I can create a new method here and I will name it sayHello. 

```Javascript
new Vue({
    el: '#app',
    data: {
        title: 'Hello World'
    },
    methods: {
        sayHello: function() {
            return 'Hello';
        }
    }
});
```

Now sayHello of course is a function and all it does is it returns hello, so it returns a string. We can take our paragraph here and execute sayHello here, don't forget the parentheses. 

```html
<p>{{ sayHello() }}</p>
```

What this will do is that whenever vuejs renders our template, it will still parse this curly brace syntax and it will then execute the function inside. Now what do you think we'll get? 

If we refresh our browser, we can clearly see hello, this happens because it's perfectly fine to execute a function in between the curly braces, the important thing is that it returns something which can be output here in the dom, so basically something which can be converted to a string. No complex object or no return value at all, it has to be something which can be converted to a string and then it's perfectly fine to call a function like this. 

Second important take away, as you can clearly see, I'm accessing sayHello in the same way I before access title, without this, without methods, without anything in front of it. So we not only have access to everything stored in the data just by typing the name here but also to anything stored in the methods property, that is also something important to keep in mind.

## Result 
Your code should now look something like: [this](https://jsfiddle.net/ministrare/38prqxjv/).

[Next -->](./Data.md)