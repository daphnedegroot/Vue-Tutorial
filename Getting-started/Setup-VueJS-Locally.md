# Vue.js

## Setup VueJS Locally

In the first course section, we ahve use JSFiddle because it allows us to really focus on the core things that we want to bring to you and that allows you to easily follow along. Now maybe you don't want to use it or you want to use a local setup right from the beginning. 

We will have a look at the real workflow later in the course.
But if you want to start locally, that is of course possible too. Simply head to the [installation page of Vue.js](https://vuejs.org/v2/guide/installation.html) and there you can download Vue.js to use it locally.

Now for a production-ready app you would of course choose the production version but for development you should use the development version which gives you some extra warnings and errors.

You can simply download this and store it in some folder. And with that you've got your files stored. Then you want to open up your favorite editor. This could be Sublime; could be Atom. And there you probably want to set up your favorite (or not your favorite but default) HTML5 skeleton inside a ``index.html``.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

And then of course we have to go to JSFiddle, copy all the HTML code and paste it in the body section, though we can remove the script import. We will use our local file for that, so let's add a script import in the head section; 

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="vue.js"></script>
</head>
<body>
    <div id="app">
        <input type="text">
        <p>{{title}}</p>  
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                title: 'Hello World!',
            },
        });
    </script>
</body>
</html>

```

I need a src of course pointing to the vue.js file. And we also need our script so let's copy that too and then add a script tag below our div, remove everyting side the src="", add this and with that if you now save this, let's say as index.html in the same folder where the vue.js file lives, you can simply double-click on it to the view it in the browser.

And of course here if you type something it should work as in JSFiddle and this is how you could follow along locally. Again a more complex workflow will be set up later, but with that, you can get started and I'd say let's
now start diving deeper into Vue.js in one of the next course modules.


[Next Chapter: Using VueJS to Interact with the DOM](./../DOM/)