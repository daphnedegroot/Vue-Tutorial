# Vue.js

## Understanding and Using Directives
Well what are directives then? If they allow us to do something like that, how could we describe them, what is a directive? 

A directive is basically an instruction you place in your code. 
Vuejs ships with a few build in directives, it aren't that many because the view it has really cover pretty much all the use cases you might want to cover and as a side note, you will learn later on how to write your own directives. 

```html
<a v-bind:href="link">
```

Back to what it is, it is an instruction and this instruction, v-bind tells vuejs bind something to my data, so bind something to the data and that includes also my functions which are stored in the vuejs instance.

```html
{{ sayHello() }}
```

So basically what we do here with the double curly braces for cases where we can't use double curly braces if you want to put it like that.

V-bind then takes an argument and generally, you pass arguments to directives by using a colon (:) and then the argument you want to pass and the argument it does expect is the attribute you want to bind, so the reference of this link here.

Well and then between the quotation marks, you just passed the property function, whatever you want to bind from your vuejs instance, the link in this case. This allows you to bind or to pass dynamic data to html attributes, something you would otherwise not be able to do.

## Result
Your code should now look something like: [this](https://jsfiddle.net/ministrare/hkt3b9gu/).

[Next -->](./V-once.md)