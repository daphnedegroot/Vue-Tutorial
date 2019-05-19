# Vue.js

## Assignment 2: Time to Practice - Events

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

Html:
```Html
<div id="exercise">
    <!-- 1) Show an alert when the Button gets clicked -->
    <div>
        <button>Show Alert</button>
    </div>
    <!-- 2) Listen to the "keydown" event and store the value in a data property (hint: event.target.value gives you the value) -->
    <div>
        <input type="text">
        <p>{{ value }}</p>
    </div>
    <!-- 3) Adjust the example from 2) to only fire if the "key down" is the ENTER key -->
    <div>
        <input type="text">
        <p>{{ value }}</p>
    </div>
</div>
```

Javascript:
```Javascript
new Vue({
	el: '#exercise',
	data: {
		value: ''
	}
});
```

## Result
Send a link of your repository (true Ryver) to your Coach after you uploaded it to Github!

[Next -->](./Write-Js-Template.md)