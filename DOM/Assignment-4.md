# Vue.js

## Assignment 4: Time to Practice - Styling

#### Shipment
- Create a repository on github and make sure the repository is set to private, untill the coaches askes you to publish it.

#### Deadline
- You will get 45 min to complete this assignment.

#### Assignment
- Clone the repository to your computer.
- Create a readme stating: 
    - The Date
    - Start time
    - End time,
- Copy the content of the code down below into a index.html file located inside the repostory`s root folder and do the same with the Javascript. (As in create a js file and make sure its linked into the indec.html).
- Do not forget to add the script tag for the Vue.js Framework.
- Follow the instructions stated in the HTML file.    

```html
<div id="exercise">
  <!-- 1) Start the Effect with the Button. The Effect should alternate the "highlight" or "shrink" class on each new setInterval tick (attach respective class to the div with id "effect" below) -->
  <div>
    <button @click="startEffect">Start Effect</button>
    <div id="effect"></div>
  </div>
  <!-- 2) Create a couple of CSS classes and attach them via the array syntax -->
  <div>I got no class :(</div>
  <!-- 3) Let the user enter a class (create some example classes) and attach it -->
  <div>
    <input type="text">
    <div></div>
  </div>
  <!-- 4) Let the user enter a class and enter true/ false for another class (create some example classes) and attach the classes -->
  <div>
    <input type="text">
    <input type="text">
    <div></div>
  </div>
  <!-- 5) Repeat 3) but now with values for styles (instead of class names). Attach the respective styles.  -->
  <div>
    <input type="text">
    <div></div>
  </div>
  <!-- 6) Create a simple progress bar with setInterval and style bindings. Start it by hitting the below button. -->
  <div>
    <button>Start Progress</button>
    <div></div>
  </div>
</div>
```

```CSS
#effect {
  width: 100px;
  height: 100px;
  border: 1px solid black;
}

.highlight {
  background-color: red;
  width: 200px !important;
}

.shrink {
  background-color: gray;
  width: 50px !important;
}

```


```JS
new Vue({
  el: '#exercise',
  data: {

  },
  methods: {
    startEffect: function() {
    
    }
  }
});
```

## Result
Send a link of your repository (true Ryver) to your Coach after you uploaded it to Github!

[Next Chapter: Using Conditionals and Rendering Lists](./../Conditionals/)