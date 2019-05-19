# Vue.js

## Using Two-Way-Binding

Time for a new project.

Create a new HTML, Javascript files and copy the content below.
Dont forget to link the Vue.js framework and the Script.js into your HTML document.

html:
```HTML
<div id="app">
  <input type="text">
  <p>{{ name }}</p>
</div>
```

```Javascript
new Vue({
  el: '#app',
  data: {
    name: 'Max',
  }
});
```
 
Before diving deeper into how we can make our properties work closer together, let's have a look at working with the template again.

We saw how we could output data, for example here with string interpolation where I output the name, we saw how we could listen to events like with key up for example, what if I wanted to do both at the same time? 

Two way data binding that would be, for example here I get this input field and I want to populate this input field with the name of the user, so with my name in this case here, on the same time whenever I change it in the input field, I want to update the data property and update it everywhere I outputted in my code for example in this paragraph. 

Turns out it's really easy to set this up with vuejs, all we need to do is add the the ``v-model directive`` to this input element. The ``v-model`` directive tells vuejs set up two way data binding for this input and then between the quotation marks, the property which we want to bind in both directions, the name in this case. 

```HTML
<input type="text" v-model="name">
```

So what this will do is it will on one hand, easy as you can see here output the name in the input field but then whenever I change it here it will listen to these changes and update the name property in my vue instance thus reflecting this change in all the places where I also use the name instance like in this paragraph.

Well, this is the missing piece when we are talking about data binding, where we were able to use the ``interpolation``, the ``v-bind`` syntax to bind two attributes, the ``v-on`` syntax to listen to events. Well now we can also use two way binding to do both at the same time.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/e9brdytq/).

[Next -->](./Computed-Properties.md)