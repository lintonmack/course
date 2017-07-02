:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## Trams

We now have the ability to create multiple `Station` instances, and the ability to pass these object instances to multiple `Route` instances. We will now create a `Tram` object. Trams will take a `Route` instance and a starting `Station` instance.

1) In `tram.js`, define an empty `Tram` constructor and prototype, as we did for our `Route` and `Station` objects:

```javascript
function Tram () {

}

Tram.prototype = {

}
```

2) Give the constructor two parameters: `route` and `startingStation`:

```javascript
function Tram (route, startingStation) {

}

Tram.prototype = {

}
```

3) Now we want to set the properties that will get added to each new instance of `Tram`. Inside the constructor, define two properties: one with the name `_route` set to the value of the `route` parameter, and another called `_currentStation`, set to the value of the `startingStation` parameter:

```javascript
function Tram (route, startingStation) {
  this._route = route
  this._currentStation = startingStation
}

Tram.prototype = {

}
```

4) Next, add a method to the prototype called `getCurrentStation`, which should return the value of `_currentStation`:

```javascript
function Tram (route, startingStation) {
  this._route = route
  this._currentStation = startingStation
}

Tram.prototype = {
  getCurrentStation: function () {
    return this._currentStation
  }
}
```

5) Lastly, we want to create a method called `drive`:

```javascript
function Tram (route, startingStation) {
  this._route = route
  this._currentStation = startingStation
}

Tram.prototype = {
  getCurrentStation: function () {
    return this._currentStation
  },
  drive: function () {
    var routeStations = this._route.getStations()
    var currentStationIndex = routeStations.indexOf(this._currentStation)
    var nextStationIndex = currentStationIndex + 1

    if (nextStationIndex >= routeStations.length) {
      return 'End of the line!'
    }

    this._currentStation = routeStations[nextStationIndex]

    return 'Now arriving at: ' + this._currentStation.getName()
  }
}
```

***
:bulb:

Let's break this down:

```javascript
var routeStations = this._route.getStations()
```

`this._route` references an instance of `Route` that we pass through our `Tram`'s constructor. This instance of `Route` inherits its parent's methods through its prototype, and therefore we can call `this._route.getStations()`, which will return an array of `Station` objects. We assign the method call to a varaible named `routeStations`, which will store the return value of the method.

```js
var currentStationIndex = routeStations.indexOf(this._currentStation)
```

We call the `indexOf` method on the `routeStations` array to find the index of the `Tram`'s current station in our `routeStations` array. We assign this to the `currentStationIndex` variable.

```js
var nextStationIndex = currentStationIndex + 1
```

The next station the `Tram` will visit will be the next element in the `routeStations` array, after the `currentStationIndex`. Therefore we just add 1.

```js
if (nextStationIndex >= routeStations.length) {
  return 'End of the line!'
}
```

If the `nextStationIndex` doesn't exist in our `routeStations` array then our `Tram` can go no further. We return out of the function.

```js
this._currentStation = routeStations[nextStationIndex]
```

Our tram hasn't reached the end of the line yet, so we set it's `_currentStation` to the next element in the array, using our `nextStationIndex`.

```js
return 'Now arriving at: ' + this._currentStation.getName()
```

Remember, our `_currentStation` always references an instance of an object. When we first call our `Tram` constructor, we pass in an object, and when we reassign to `_currentStation` above, we are assigning an object from an array of objects. Therefore, we can call methods on this object that exist on its parent's prototype. In this case we call `getName()` on the `Station` object - we concetenate this onto a helpful string, and return from the method with the string.
***

## Taking our `Tram` for a `drive` :wink:

Save your file and try it out in the Chrome console. 

1) Use the commands you typed on the last page to add stations, create a route, and add stations to that route. 
2) Then create a new instance of `Tram` passing in the route as the first argument, and the first station you added to your route as the second argument.
3) Then call `getCurrentStation` and `drive` methods on the `Tram` instance.

![New Tram](images/newTram.png)

***
:bulb:

Instead of:

```js
var tram = new Tram(piccadillyToHoltTown, piccadillyStation)
```

You could do:

```js
var tram = new Tram(piccadillyToHoltTown, piccadillyToHoltTown.getStations()[0])
```

This is essentially just calling the `getStations()` method on the `piccadillyToHoltTown` instance of `Route`, which we know returns an array of `Station` objects. We then access the first station object with `[0]`.
***

## Add, commit and push.

## Finished?

If you have finished then why not add some more functionality?

### 'This is the service from Eccles to Ashton-under-Lyne. Now arriving at: Holt Town'
* Add a method to the `Route` prototype called `getStartingStation`, which returns the first station in the `_stations` array.
* Add a method to the `Route` prototype called `getTerminatingStation`, which returns the last station in the `_stations` array.
* Modify the `Tram`'s `drive` method return value so it includes the starting and terminating stations for that route.