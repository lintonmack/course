:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

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

3. `expect` `port.getShips()` `toContain` `ship`:

```js
it('can embark ships', function () {
  expect(port.getShips()).toContain(ship)
})
```

4. Run the tests. You should fail with the error `TypeError: port.getShips is not a function`.

5. Create the `getShips` method (but don't pass the test!).

6. Run your tests. The error you should now have is: `Expected undefined to contain Object({ _currentPort: Object({ _weather: Object({ _NOT_STORMY_PROBABILITY: 0.5 }) }) }).`