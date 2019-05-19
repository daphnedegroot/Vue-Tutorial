# Vue.js

## Binding to Attributes

You should feel a bit more confident with this first syntax with the double curly braces, we used quite a lot and I think it's clear what it does.

What if you wanted to do something else? \
Let's say we have a link property and as the name implies, it stores a link to let's say Google.com. 
```Javascript
new Vue({
  el: '#app',
  data: {
    title: 'Hello World!',
    link: 'http://www.google.com',
  },
  methods: {
    sayHello: function() {
      return this.title;
    }
  }
});
```
Now here in the paragraph, we might not only want to say hello, we also might want to output this link so we could enter an anchor tag and call it Google since this link leads to Google and then we could try the following, use our double curly braces in the ref attribute to that output, the link. 

```html
<p>{{ sayHello() }} - <a href="{{ link }}">Google</a></p> 
```

If I hit control enter, we got our link here but if I click on it, well you see it's not going to google at all. What it actually does is it encodes the curly braces and tries to go to curly brace, curly brace, whitespace link, whitespace curly brace, curly brace so it tries to parse this as a link.

That is the normal thing to happen because vue.js doesn't work like that, we can't use curly braces in any html element attribute, so this does not work. We can only use these curly braces in the place where we would normally use text, not on html elements.

What if we still wanted to bind this link dynamically?
That is certainly a use case you will oftentimes see in your application, no worries, you can do this. We can bind it dynamically by removing the link for now and then introducing a directive vuejs ships with, this directive is called a ``v-bind`` and this directive tells vue.js hey don't use the normal attribute here, don't use it like a normal html attribute, instead bind it.

```html
<p>{{ sayHello() }} - <a v-bind:href="link">Google</a></p> 
```

We do pass an argument to the bind directive by adding a colon and the argument we do pass is then the name of the attribute we want to bind,
so ref here. By setting it up like this we can now pass a link here between the quotation marks, no curly braces still, this is the link, we don't need curly braces because we now already are in vuejs template language. And with this, if I now hit control and I now try to load this, well you see I'm now taken to Google because now it binds to this data dynamically due to this v-bind directive.


## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/hkt3b9gu/).

[Next -->](./Directives.md)