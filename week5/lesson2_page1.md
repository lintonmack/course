# Metrolink continued

In the previous lesson, we created 3 objects: `Station`, `Route` and `Tram`. We gave each object's prototype its own methods, and we gave each instance of the object its own properties. Then we called those methods and `console.log`gged out the current state of our application as the object methods were called. Now we want to reflect those changes on the DOM.

We're going to represent an entire Metrolink route on the page, and we will have a **Next Station** button, which moves us along the route.

:twisted_rightwards_arrows: **Try and remember who was last to drive and navigate last time (your Git commit history may help) and switch roles.**

## CSS

We're going to need some basic CSS, just to make our Tram application a bit more visually appealing. Create a **style.css** file in the top level of your project folder, and add a `link` tag in your **index.html** to point to the file.

Copy in and save the following (copying and pasting is normally to be discouraged, but we want to focus on the JavaScript over the CSS at this point):

```css
body {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
  padding: 20px;
}

.station {
  overflow: hidden;
}

.circle {
  border-radius: 50%;
  width: 20px;
  height: 20px;
  border: 3px solid #000;
  margin: 20px;
  float: left;
}

.circle.-current {
  background-color: yellow;
}

.name {
  font-size: 20px;
  margin: 20px;
  float: left;
  font-weight: bold;
}
```

After saving, be sure to add and commit with a significant message for the change (i.e. 'added styles').

## HTML wrapper

Because we'll be adding to the DOM, we'll need to add a couple of buttons to execute our `Tram` methods and also we'll need to create an element with an ID so we can populate it with data from our application. Inside **index.html** add the following above your `script` tags, inside your `body`:

```html
<h1>Metrolink</h1>
<button id="nextStationBtn" type="button">Next Station</button>
<button id="reset" type="button">Reset</button>
<div id="stations"></div>
```

We will access the IDs `nextStationBtn`, `reset` and `stations` in JavaScript.

## The JS file responsible for "printing"

We want to create a file where we handle the rendering of our application's *state* to the DOM. Create a new file inside your `/js` folder called `printer.js`. Inside your `index.html` - after your `script` tags for `station.js`, `route.js` and `tram.js` - add a new `script` tag and include in `js/printer.js`.

## jQuery

We'll be using jQuery to append to the DOM. Add the following `script` tag above your other script tags to bring jQuery in from a content delivery network:

```js
<script
  src="https://code.jquery.com/jquery-3.2.1.min.js"
  integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
  crossorigin="anonymous"></script>
```

## Create a `Route` from an array of `Station`s

Next, we want to create an array with all of our stations. Each element in our array will be a String of a station's name. After we've defined the array, we'll loop through it and create a `Station` object from each element.

1) Firstly, inside `printer.js`, define a variable called `stationNames` and assign to it an empty array:

```js
var stationNames = []
```

2) Next, populate it with the names of all of the stations on a Metrolink tram route (in the same order as in reality). Each element in the array should be of *String* type:

```js
var stationNames = [
  'Altrincham', 
  'Navigation Road', 
  'Timperley', 
  'Brooklands', 
  'Sale',
  'Dane Road',
  'Stretford',
  'Old Trafford',
  'Trafford Bar',
  'Cornbrook',
  'Deansgate-Castlefield',
  'St Peter\'s Square',
  'Piccadilly Gardens',
  'Piccadilly',
  'New Islington',
  'Holt Town',
  'Etihad Campus',
  'Velopark',
  'Clayton Hall',
  'Edge Lane',
  'Cemetery Road',
  'Droylsden',
  'Audenshaw',
  'Ashton Moss',
  'Ashton West',
  'Ashton-under-Lyne'
]
```

3) Once you've defined your `stationNames` variable and you've assigned an array of station names then define a new variable to represent your route (name it as such). Assign to it a `new` instance of `Route`:

```js
var altrinchamToAshtonUnderLyne = new Route()
```

4) Now we're going to use jQuery's `.each` utility method. The `.each` method will go through every item in an array, and for each item it will call the callback we provide, passing the index of the current element, and the current element's value as arguments. In this case, we want to loop through `stationNames`, and we provide a callback function which accepts the index and value of each `stationNames` element, and passes it to a `Route` instance's `addStation` method:

```js
var stations = $.each(stationNames, function (stationIndex, stationName) {
  altrinchamToAshtonUnderLyne.addStation(new Station(stationName))
})
```

***
:bulb:

Why create an array of Strings, only to loop through them and create objects from them afterwards? Why not just create an array of `new` Objects? The reason is so we can keep our code **DRY**. DRY is short for *Don't Repeat Yourself* and it really does speak for itself. The key concept is trying to save yourself as much code as possible. In this case, by looping through an array with `.each` and using each element in that array to create a new object, we save ourselves from having to type `new Station` repeatedly. 
***

## Instantiating a new Tram

Now we have `Station`s and a `Route`, we can pass our `Route` to a new `Tram`.

1) Define a new variable called `tram` and assign it a `new Tram()`. Our `Tram` constructor takes 2 arguments: the `route` it should follow, and the `startingStation`. Pass in `altrinchamToAshtonUnderLyne` as the route (unless you named it differently) and for the `startingStation`, pass in `altrinchamToAshtonUnderLyne.getStations()[0]` (call `getStations` on the route, and retrieve the first item of the returned array a.k.a the first `Station` object on the route):

```js
var tram = new Tram(altrinchamToAshtonUnderLyne, altrinchamToAshtonUnderLyne.getStations()[0])
```

## Add, commit and push.

:twisted_rightwards_arrows: **Switch Driver/Navigator roles.**
