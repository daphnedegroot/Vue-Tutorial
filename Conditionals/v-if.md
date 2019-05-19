# Vue.js

## Conditional Rendering with v-if

We start in a brand new project, very simple as can see down here, just my vue instance which has this show property in a data field and then two paragraphs in my div here. So if we run this, we see you can see me and do you also see me? Now as these texts already imply, we're now going to work with conditionally showing and hiding or attaching and detaching elements to the dom, that's a task you'll probably see in all the applications you've built, you don't want to show everything on your template all the time.

HTML:
```html
<div id="app">
  <p>You can see me!</p>
  <p>Do you also see me?</p>
</div>
```

JavaScript:
```JS
new Vue({
  el: '#app',
  data:{
    show: true
  }
});
```

Sometimes you only want to show an error message, let's say in case of a wrong input, in a form input or something like that, so you want to conditionally shows certain messages or elements on your page. Now vuejs of course include some methods to allow you to easily do that, so let's dive into them and have a look at them and I'm going to start with ``v-if``. That's a directive we can add to a paragraph or to any element  and it allows us to bind it to a condition or to a property, whatever which resolves to true or false, in the end this is the important thing. So I could bind it to show here to well show this since this is set to true. 

```html
<div id="app">
  <p v-if="show">You can see me!</p>
  <p>Do you also see me?</p>
  <button @click="show=!show">Switch</button>
</div>
```

If I now add a button where I say switch or whatever you like and then add a click listener where I set show to
well the opposite of show, so I basically switch it. If I now save this, you can see that once I hit this button, you see the you can see me text disappear and now it's back there. Important thing, if we inspect this, this is the paragraph element, if I now hit switch, you see it disappeared entirely, we only get this comment left which kind of shows us that something was there but it is gone.

It's not hidden, it's not transparent, it's gone and this is important to understand, ``v-if`` really attaches or detaches elements to the dom. It not just hides them, it completely removes them if you well have a false condition here or if the condition returns false here. ``V-if`` can also be extended, I'll add a new paragraph, now you see me and I'll add v-else, v-else will automatically refer to the latest v-if in front of it, so this one here and if we compile these, you see that we switch now between now you see me and you can see me, so I show the else condition whenever the v-if condition is false, which makes sense like a normal if else statement.

Notice you don't have v-elseif and so on, you would simply need to create a new v-if statement if you want to check multiple conditions. This is just a shortcut if you know you got an either or decision, then v-if and v-else allows you to quickly get started and set this up.
Also notice, v-if shows the entire element and all nested elements, so if I nest an element inside this paragraph, for example this span, well this is also affected by it.

So it really removes the complete element and all nested elements, not just the element leaving behind the nested ones, no, that's not how it works. Everything gets removed or attached, whatever the condition says.

## Result
Your code should now look something like: [this]().

[Next -->](./v-else-if.md)