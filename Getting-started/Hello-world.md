# Vue.js

## Hello World!
Getting started with Vue.js and creating your first application is actually very simple. \
Lets go ahead to [vuejs.org](http://vuejs.org), it's official home page, and there you`ll see this nice: "GET STARTED" button. Let's click on it. It should take you to the official documentation, which is always worth having a look anyways, but there we want to go to installation section.

Now here you've got a couple of different options depending on which kind of setup you want to use. Later in this course we'll use a more complex setup using Webpack to bundle all our files, but let's start with a simple one.

You could either simply download Vue.js or, as I want to do now, simply grab it from a CDN (so imported from another server). Here I'll take the first one and then simply copy the html script tag with the link. 

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Now with the link, we can import it to get access to Vue.js. 
Let do this on [JSFiddle](http://jsfiddle.net/); which is kind of a Web editor, for a very simple JavaScript, HTML and CSS-only projects. Here we got our HTML section in which we should paste the copied HTML script tag with the CDN link.

You could leave the link untouched, or you can simply remove the version number to always automatically fetch the latest version from the cdn.

With that we imported Vue.js and we can now already use it and all its features. So let's use it and build our first little application. For that,
I want to add a paragraph in which I want to say Hello World!

```html
<p>Hello World</p>
```

Now saving it like this clearly is not very interesting.
There is no JavaScript involved at any place. Instead we want to output this through Vue.js. Now in order to do so, I will simply go to the JavaScript section and use the import function for one of the major objects, the Vue.js framework gives me; the Vue object.

Let's create a new instance based on that with the ``new`` keyword and then ``Vue``.

```Javascript
new Vue
```

This gives us a new Vue instance and Vue instances created like this are the core of each Vue application, of each piece of code you want to use Vue.js in. You create such instances and then these instances have one major job; control their own template of code, of HTML code, which they render to the screen. 

Now in order to let this Vue instance do this, we have to pass an argument to this constructor function. The argument is a JavaScript object and then we have one very important property Vue.js will recognize; the ``el`` property. This is kind of a reserved property obviously. Vue.js will recognize it and ``el`` takes a string as a value. 

```Javascript
new Vue ({
	el: '',
});
```

With this string we set up which part of our HTML code here should be under control of this Vue instance. And with under control, I mean we can then change it through this Vue instance. 
Since we want to control the HTML ``p`` element, we need to wrap it in a div let's say, a div which encloses my template for this Vue instance. So in the HTML section above the ``P`` element, I'll add a ``div#app`` and then tab automatically gives me a div with id="app". Insert the paragraph inside of the newly created div. 

End result:
```HTML
<div id="app">
  <p>Hello World!</p>  
</div>
```

Now we can select this div inside the JavaScript section with id="app" by using this string like a CSS selector inside the JS section of the editor.

End result:
```JavaScript
new Vue ({
	el: '#app',
});
```

With '#app' we select the element with the id="app". 
If we would have used '.app', we would have selected the first element with class="app". Therefore, we have now control of this div. It is now the template of this Vue instance. And now in order to output something we need some data.

Vue.js has got a special property for this, the ``data`` property (another reserved property) and now this isn't a string, **it's an object instead**.  And in there we store all the data we want to use in this Vue instance.

```javascript
new Vue ({
	el: '#app',
  data: {
  	
  },
});
```

So let's say we want to have a title, and this name is totally up to you,
where I say Hello World! Now is the title I want to output in my template and before I hardcoded it in here,

```javascript
new Vue ({
	el: '#app',
  data: {
  	title: 'Hello World!',
  },
});
```

now with this template being under control of Vue.js, it's as simple as using this special syntax Vue.js will recognize, with double curly braces (opening and closing) and in between I can simply write title and Vue.js will automatically look into this data object (as I said this is a reserved word), look into this object, find the title property and output it here.

```html
<div id="app">
  <p>{{title}}</p>  
</div>
```

If we now hit Ctrl-Enter in JSFiddle to see the result we see Hello World! on the right because now we're outputting this title through Vue.js which now controls this template.

### Result
Your code should like something like this:
- [End Result](https://jsfiddle.net/ministrare/gnjy3mkv/)


[Next -->](./Extending-the-VueJS-Application.md)