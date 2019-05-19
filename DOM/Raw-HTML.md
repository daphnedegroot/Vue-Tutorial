# Vue.js

## How to Output Raw HTML

Let's enhance it even more!

let's say we also have a finished link property here and unlike the link, this is not just the URL but it is the complete anchor tag. 

```javascript
new Vue({
  el: '#app',
  data: {
    title: 'Hello World!',
    link: 'http://www.google.com',
    finishedLink: '<a href="http://www.google.com">Google<a/>',
  },
  methods: {
    sayHello: function() {
    	this.title = 'Hello!';
      return this.title;
    }
  }
});
```

We can write html code here too, just like that and this should also lead to google.com but of course the important thing here is that it is the complete link and not URL as I just mentioned.

So we could enter a horizontal line here and below that horizontal line, have another paragraph where I simply want to output this finished link to get this link to Google.

```html
<div id="app">
  <h1 v-once>{{ title }}</h1>
  <p>{{ sayHello() }} - <a v-bind:href="link">Google</a></p> 
  <hr>
  <p>{{ finishedLink }}</p>
</div>
```

What do you think we'll see if I now hit refresh? Well let's find out. We see the link as text, we don't see a finished or a rendered html element, instead we see the html element in text form. 

This is the default behavior of vuejs and this is great that it is the default behavior because this behavior ensures that we don't run into any problems with cross-site scripting attacks. By default vuejs escapes vuejs which means it doesn't render html elements, it only renders text, most of the time that is what you want.

But if you got some html content where you know the source where it is coming from is safe or you did sanitize it on your own before outputting it, well in such a case, you might want to output the html code and not just the text. Think of a blog post which might have some editing inside of it, for such a use case, you can get rid of the interpolation syntax with the curly braces and instead use another directive.

The directive would then be placed on the element where you want to output the html code and it is called the ``v-html``. This allows you to then pass the name of the property here which holds the html code. 

```HTML
<p v-html='finishedLink'></p>
```

If I now hit refresh, you now see the link, ``v-html`` tells vuejs to actually render html code and not escape it. Again use this carefully, it does expose you to cross-site scripting attacks, if this is possibly some content which for example gets created by your users and thus you can't control what is placed inside of it. If you know the source is clean or you sanitized it on your own, you should be good to go and this is how you can output normal html through vue.js.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/mpej89x7/).

[Next -->](./Assignment-1.md)