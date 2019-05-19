# Vue.js

## Assignment 3: Time to Practice - Reactive Properties

#### Shipment
- Create a repository on github and make sure the repository is set to private, untill the coaches askes you to publish it.

#### Deadline
- You will get 15 min to complete this assignment.

#### Assignment
- Clone the repository to your computer.
- Create a readme stating: 
    - The Date
    - Start time
    - Endtime,
- Copy the content of the code down below into a index.html file located inside the repostory`s root folder and do the same with the Javascript. (As in create a js file and make sure its linked into the indec.html).
- Do not forget to add the script tag for the Vue.js Framework.
- Follow the instructions stated in the HTML file.    

```html
<div id="exercise">
    <!-- 1) Show a "result" of 'not there yet' as long as "value" is not equal to 37 - you can change "value" with the buttons. Print 'done' once you did it -->
    <div>
        <p>Current Value: {{ value }}</p>
        <button @click="value += 5">Add 5</button>
        <button @click="value += 1">Add 1</button>
        <p>{{ result }}</p>
    </div>
    <!-- 2) Watch for changes in the "result" and reset the "value" after 5 seconds (hint: setTimeout(..., 5000) -->
    <div>
        <input type="text">
        <p>{{ value }}</p>
    </div>
</div>
```


```JS
new Vue({
    el: '#exercise',
    data: {
        value: 0
    }
});
```

## Result
Send a link of your repository (true Ryver) to your Coach after you uploaded it to Github!

[Next -->](./Dynamic-Styling-CSS-Classes/Basics.md)