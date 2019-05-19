# Vue.js

## Extending the VueJS Application
Now in the last chapter, we already created our first Vue application and got started with it. Now let's enhance it a little bit more before we
dive much deeper into it in the next course chapters.

So what I want to do right now though is I want to add an input field.
I can do this by typing input and hitting tab which will give me that JSFiddle and your HTML section should now look something like this:

```html
<div id="app">
<input type="text" v-on>
  <p>{{title}}</p>  
</div>
```

Let say that we want to allow the user to type something inside the input and update my title depending on what the user enters. We can do this by adding a command to this input field ``v-``, an instruction Vue.js will recognize what is called a **directive**. The directive we need is ``v-on`` and this is just set a special command Vue.js will recognize.

Keep in mind that the ``<div id="app">`` part is under control of Vue.
And then the thing this v-on command tells Vue.js is,please listen to some event. Now which event?

I pass this as an argument and arguments are passed to directives by adding a colon and then the name of the argument; in this case the name of the event we want Vue to listen to. It's the ``input`` event which is fired on every keystroke. And then we assign a value to this and between the quotation marks we would now write the code which we want to execute whenever the inputfield gets updated. So here what I want to do is, I want to call a method and calling a method is very simple. I can simply call ``changeTitle`` here.

```html
<div id="app">
<input type="text" v-on:input="changeTitle">
  <p>{{title}}</p>  
</div>
```

Now of course this method doesn't exist yet, so let's create it. Creating methods is simple. As with ``data``, Vue.js has also got a reserved property in the Vue instance which is called ``methods``; and no worries, you will learn about all these reserved property names and how they work throughout the course. 

```JavaScript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
  methods: ,
});
```

Methods is again an object and here we simply set up all the methods we want to use either in our template or from within our Vue instance.

```Javascript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
  methods: {
      
  }
});
```

Because we named it ``changeTitle`` in the HTML section, we need to use the same name down here. This is a function and want this function to change my title. 

```Javascript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
  methods: {
  	changeTitle: function()
    {
        this.title = ,
    },
  }
});
```

And here's the first important thing, I won't say ``data.title`` or something like that; Instead I can say ``this.title =``. Now ``'this'``(referring to the data object) certainly looks a bit strange and it is strange. It's some magic being done in the background by Vue.js. It proxies all our data properties like title to the top Vue instance object automatically; which is why we can access it with ``'this'``.

I will come back to this later in the course, but for now it's just important to keep in mind you got access to all the properties stored in data and also to all the methods stored in methods by accessing them with this. and then the name. So ``this.title`` gives me access to the title stored inside data and now I want to assign you value to user entered into the input. 

Well thankfully, as with vanilla JavaScript, there is this event object being created automatically for me. This has nothing to do with Vue.js, this is vanilla JavaScript and how that DOM works. I get this event object which, for example, also stores the target of the event which of course will be this input field. Now this event object which is created automatically by JavaScript is passed to this method automatically by Vue.js. So we can fetch it because we know it will receive an argument and we`ll name it event. This again is this default event object created by JavaScript.

```Javascript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
  methods: {
  	changeTitle: function(event)
    {
        this.title = ,
    },
  }
});
```

Now you can simply say event. I know that this default object has a target property and I know that the target will be the input field of which I know it will have a value property holding the value the user entered.

```Javascript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
  methods: {
  	changeTitle: function(event)
    {
        this.title = event.target.value;
    },
  }
});
```

Well and with this in place, that's all if we now Ctrl-Enter again we see this input and if we type something there we see that it updates our title. This is awesome I'd say. This is our first Vue.js application and we built. Really awesome! So with that, let's see how you can work your way through this course, what this course has to offer, how you could set up the same example locally on your machine, before we then dive super-deep into Vue.js and the next chapters.

### Result
Your code should like something like this:
- [End Result](https://jsfiddle.net/ministrare/gnjy3mkv/11/)

[Next -->](./Setup-VueJS-Locally.md)