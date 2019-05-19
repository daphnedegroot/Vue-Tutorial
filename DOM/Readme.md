# Vue.js

- Using VueJS to Interact with the with the DOM
    - [Understanding VueJS Templates](#Templates)
    - [How the VueJS Template Syntax and Instance Work Together](./Template-instance.md)
    - [Accessing Data in the Vue Instance](./Data.md)
    - [Binding to Attributes](./Binding-Attributes.md)
    - [Understanding and Using Directives](./Directives.md)
    - [Disable Re-Rendering with v-once](./V-once.md)
    - [How to Output Raw HTML](./Raw-HTML.md)
    - [Opdracht 1: Time to Practice - Outputting Data to Templates](./Assignment-1.md)
    - [Listening to Events](./Listen-to-Events.md)
    - [Getting Event Data from the Event Object](./Getting-Event-Data.md)
    - [Passing your own Arguments with Events](./Arguments-with-Events.md)
    - [Modifying an Event - with Event Modifiers](./Event-Modifiers.md)
    - [Listening to Keyboard Events](./Keyboard-Events.md)
    - [Opdracht 2: Time to Practice - Events](./Assignment-2.md)
    - [Writing JavaScript Code in the Templates](./Write-Js-Template.md)
    - [Using Two-Way-Binding](./Two-Way-Binding.md)
    - [Reacting to Changes with Computed Properties](./Computed-Properties.md)
    - [An Alternative to Computed Properties: Watching for Changes](./Alternative-Computed-Properties.md)
    - [Saving Time with Shorthands](./Shorthands.md)
    - [Opdracht 3: Time to Practice - Reactive Properties](./Assignment-3.md)
    - [Dynamic Styling with CSS Classes - Basics](./Dynamic-Styling-CSS-Classes/Basics.md)
    - [Dynamic Styling with CSS Classes - Using Objects](./Dynamic-Styling-CSS-Classes/Objects.md)
    - [Dynamic Styling with CSS Classes - Using Names](./Dynamic-Styling-CSS-Classes/Names.md)
    - [Setting Styles Dynamically (without CSS Classes)](./Styles-Dynamically.md)
    - [Styling Elements with the Array Syntax](./Styles-Array.md)
    - [Opdracht 4: Time to Practice - Styling](./Assignment-4.md)
    - [Module Wrap Up](./Summary.md)

## Templates
Starting Code:
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script scr="Vue.js"></script>
</head>
<body>
    <div id="app">
        <p>{{ title }}</p>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                title: 'Hello World'
            },
        });
    </script>
</body>
</html>
```

Back with a brand new project though a very simple one as you can tell, I do have my paragraph where I output a title and the title is simply is hello world here.

So pretty much the same as we had in the first module, just different text, a little bit leaner, no event as of now because what I want to start with is this connection between this vue instance and this html code.

I already explained that we have this kind of connection but there is one important thing to understand which I want to highlight right now, by creating this new vuejs instance and note that we don't store in any variable, it is still created though by instantiating this instance, we do create this connection and Vue.js then takes this html code up there and creates a template based on that code. And this is important to understand, Vue.js does not add runtime, use our html code and have these commands in our html code.

You can actually see this if we inspect this hello world text here, then you'll see that here of course we only have hello world, we don't see any curly braces, we don't see any other code which was added by Vue.js, no hidden hint that there would be some magic going on, nothing at all. Vue.js creates a template based on our hmtl code, stores that internally and then basically uses this template to create the real html code which then is rendered as the dom.

This is important to understand because this allows us to use template syntax like that and like all the other things we will teach you throughout this course, in the html code we write because it's not the one running in the browser in the end, there is this layer in the middle and this layer is the Vue.js instance which takes our html code, creates a template, renders this template by for example entering the title here and then outputs the final html code which gets rendered here. 

You might have been aware of that already but if not, this is really important to understand why we were able to write the code. With that out of the way, let's dive deeper into how we can interact with the dom through this template approach by using Vue.js.

[Next -->](./Template-instance.md)