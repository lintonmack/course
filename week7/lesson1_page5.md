:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

Feel free to switch roles as often as you see fit for this part of the walkthrough.

## I don’t want my ship to dock at a port if the port is full

```
As a ship captain,
So I can dock my ship,
I don’t want my ship to dock at a port if the port is full.
```

## Ports have capacity

Our user story states that a port can be full. This creates a problem for us as it means ports now need to know which ships are docked with them. 

1. In `PortSpec.js` in the `describe` callback, declare a new variable `ship`, and inside the `beforeEach` callback, assign a new instance of the `Ship` object to `ship` passing in `port`:

```js
  var weather
  var port
  var ship

  beforeEach(function () {
    weather = new Weather()
    port = new Port(weather)
    ship = new Ship(port)
  })
```

2. Add a new test `can embark ships`:

```js
it('can embark ships', function () {
  
})
```

3. Call `embark` on `port`, passing in `ship`, and then `expect` `port.getShips()` `toContain` `ship`:

```js
it('can embark ships', function () {
  port.embark(ship)

  expect(port.getShips()).toContain(ship)
})
```

4. Run the tests. You should fail with the error `TypeError: port.embark is not a function`. Go ahead and create the `embark` method to get rid of the error.

5. Run your tests again. You should now fail with the error `TypeError: port.getShips is not a function`.

5. Create the `getShips` method (but don't write any more than you need to - just enough to pass the error).

6. Run your tests. The error you should now have is: `Expected undefined to contain Object({ _currentPort: Object({ _weather: Object({ _NOT_STORMY_PROBABILITY: 0.5 }) }) }).`. We can now go ahead and write the code to pass our failing test.

7. Our `Port` has ships, so we can assume that these will be stored in an array on the `Ship` constructor. Add a new property to `Port` named `_ships` and assign to it an empty array.

8. Now inside your `getShips` method, return the value of your `_ships` property.

3. Run your tests. They should still fail - now with the error: `Expected [  ] to contain Object({ _currentPort: Object({ _weather: Object({ _NOT_STORMY_PROBABILITY: 0.5 }), _ships: [  ] }) }).`. 

4. Before, our `getShip` method was returning `undefined` and now it's returning an empty array. The reason the array is still empty is because we haven't actually put a ship in it yet. We can see from our test that `embark` takes a `ship` so go ahead and add the code to that method that `push`es `ship` into the `_ships` array.

5. Now run your tests. If you've done everything correctly, you should now be passing.

## A ship docks, a port embarks it

Think about a ship in real life. It sails itself to the port - the port doesn't pull it in. Our `Port` still has to keep track of the `Ship` though. Therefore, when our `Ship` is ready to `dock` at the port, we need to instruct `Port` to `embark` our `Ship`. We could do this manually, but it'd be much more user-friendly if `embark`ing at the port was  handled automatically for us, as its something we'll always need to do when we `dock` a ship: we need to test that our objects are calling methods on other objects - in this case that `Ship`'s `dock` method calls `Port`'s `embark` method.

1. Inside `Ship.js` create a new test `is instructs the Port to embark`:

```js 
it ('instructs the Port to embark', function () {

})
```

2. Now we want to `spyOn` `arrivalPort`'s `embark` method: 

```js
it('instructs the Port to embark', function () {
  spyOn(arrivalPort, 'embark')
})
```

Jasmine will now listen in on `arrivalPort.embark()`.

2. Now call the `dock` method on `ship` and pass in `arrivalPort` as the only argument:

```js 
it('instructs the Port to embark', function () {
  spyOn(arrivalPort, 'embark')

  ship.dock(arrivalPort)
})
```

3. Finally, we want our assertion. Call `expect` and pass in `arrivalPort.embark`. Then on the `expect`'s returned object, call the `toHaveBeenCalledWith` method and pass in `ship`:

```js 
it('instructs the Port to embark', function () {
  spyOn(arrivalPort, 'embark')

  ship.dock(arrivalPort)

  expect(arrivalPort.embark).toHaveBeenCalledWith(ship)
})
```

***
:bulb:

First of all here with `spyOn(arrivalPort, 'embark')`, we tell Jasmine to listen in (*spy*) on an object's method (`arrivalPort.embark()`). It will keep spying on this method until the test has finished.

Then we go ahead and ready ourselves for the assertion. We call `ship.dock(arrivalPort)`. Our spy is still listening, whilst this method executes.

Finally, we make an assertion the method we're spying on that it has been called (with an argument): `expect(arrivalPort.embark).toHaveBeenCalledWith(ship)`
***

4. Run your tests. We should be rightly failing again: `Expected spy embark to have been called with [ Object({ _currentPort: Object({ _weather: undefined, _ships: [  ], embark: spy on embark }) }) ] but it was never called.`. Our test is telling us that it expect's the `arrivalPort`'s `embark` method to have been called. 

The only piece of our application's code we run in our test is `ship.dock(arrivalPort)`, so the only way we can make this test pass it to call the `Port`'s `embark` method inside of our `dock` method.

5. Inside `Ship.js`, find your dock method, and at the end call `embark` on `port` and pass in `this` (the current instance of the ship):

```js
dock: function (port) {
  this._currentPort = port

  port.embark(this)

  return
}
```

6. Run your tests. You should be green.

## Ports have capacity

"I don’t want my ship to dock at a port if the port is full."

Our port now knows what ships are docked in it, but it doesn't set a limit. We will say for the sake of this exercise that every port has a capacity of 8.

1. Inside your `PortSpec.js`, add a new test `has a capacity`.

2. `expect` `port.getCapacity()` `toEqual` `8`.

3. Run the tests. The test `has a capacity` should fail. Use the top error of your stack trace to guide you, and go ahead and write the code to make the test pass.

:exclamation_mark: Ask for your capacity code to be reviewed before you go any further!

## Full capacity!

4. Now inside `ShipSpec.js`, create a new test `doesn't dock if port at capacity`.

5. Inside your test's callback, `dock` a `ship` at a `port` 8 times (use a for loop to do this!). Your port will now be at capacity.

6. Now, still inside the callback, `expect` that when you `dock` a `ship` at a `port` it will throw an error `port is at capacity`.

7. Run your tests. This test should fail. Again, write the code to make the test pass (hint below).

***
:bulb:

This is a hard one. 

1. `getShips` that the `port` has.
2. Check if: 

```
getShips returned array length + 1 *is greater than* the port's capacity.
```
3. If yes (`true`) then throw an error.
***

## Add, commit and push

[Summary](lesson1_summary.md)