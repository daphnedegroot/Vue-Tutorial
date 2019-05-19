# Vue.js

## Getting started

- Getting started
    - [Introduction](#Introduction)
    - [Hello World!](./Hello-world.md)
        - [Result](./Hello-world.md#Result)
    - [Extending the VueJS Application](./Extending-the-VueJS-Application.md)
        - [Result](./Extending-the-VueJS-Application.md#Result)
    - [Setup VueJS Locally](./Setup-VueJS-Locally.md)

### Introduction
Vue.js is an amazing powerful and really fun to work with front and framework.\
Let's dive into the first important question: \
- What is Vue.js or why would you want to use it? 
- How does it help you?

Vue.js allows you to create everything from small widgets driven by Javascript which you drop into existing applications over medium sized applications where you control the whole page through Javascript and therefore re-render various parts making it very reactive all the way up to building big enterprise level applications single page applications where your whole Web page multiple pages (Or so does it feels for the user) are driven by Vue.js which renders significant parts of the DOM to make it look like there were different pages being loaded but in the end Javascript handling all of that.

**Why javascript?** \
Because javascript runs in the browser you don't need to reach out to any server you don't need to wait for any responses if you only want to rerender parts of the application. This makes the application very reactive, it makes it feel nice and it provides awesome user experiences.

Now why would you choose Vue.js and not let's say angular2 or react.js which you might know, can do a similar thing.
Well first of all Vue.js is extremely lean and small regarding a file size.
We're talking about 16 kilobytes minified and gzipped for the core framework. This is without the router for example which you would have to add extra. But even with that it still stays very lean and small.

It's a very focused and to the point framework but it's not only small hands providing a fast loading time. It also is fast at runtime and telling by some benchmarks it even beats angular2 and react.js. Now of course that will always depend on your specific application, but what we can say is it is extremely fast add runtime hence really again adding to this very great reactive user experience. Now you would probably assume that a small and fast framework doesn't have that many features but you would be wrong. It's a very feature rich and throughout the course we will go through all the features and you will learn how they work how you use them when you use them. What the idea behind them is. You will learn that Vue is very extendable for example with the extra router but then this extension then also fits nicely into the core framework.

[Next -->](./Hello-world.md)