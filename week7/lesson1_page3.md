:twisted_rightwards_arrows: **Driver and Navigator switch roles if you haven't already done so**

## The weather

```
As a ship captain,
To ensure the safety of my passengers,
I don’t want my ship to set sail if the weather is stormy.
```

1. Create a new file in `spec/` called `WeatherSpec.js`.
2. Include the file into `SpecRunner.html`, underneath your `ShipSpec.js` include.
3. Call Jasmine's `describe` function, passing `Weather` as the first argument, and an anonymous function as the second:

```js
describe('Weather', function () {

})
```

4. Inside the `describe` callback, declare a new variable `weather`. Now in a `beforeEach` call, pass an anonymous function, and inside instantiate a new Weather object, assigning it to `weather`:

```js
describe('Weather', function () {
  var weather

  beforeEach(function () {
    weather = new Weather()
  })
})
```

## isStormy

`isStormy` will make a random decision as to whether the weather is stormy or not, using JavaScript's [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random). `Math.random()` will return a floating-point (decimal place) number between 0 and 1. We will assume that any number less than (`<`) 0.5 will equate in stormy weather (not a great probability for our holidaymakers!). 

Because the probability is random, we face a problem by which we don't actually know what the outcome of our `isStormy` method is, which begs the question: how do we test it? The answer is to listen in (*spy*) on `Math.random()`. When it's called, we will modify its return value so we can dictate what `isStormy` returns.

1. Inside our `describe`, after the `beforeEach`, call `it` and pass in a description of `can be stormy`. Pass in an anonymous function as the second argument:

```js
  it('can be stormy', function () {

  })
```

2. Now we need to create our spy. Call Jasmine's `spyOn` function. The first argument is the object you wish to spy on, and the second argument is the method on that object. We want to listen in on the `Math` object, and it's `random` method. The `spyOn` function returns an object with an `and` method, which also returns an object with a `returnValue` method, which will modify the `random` method's return value. Lets have a look:

```js
  it('can be stormy', function () {
    spyOn(Math, 'random').and.returnValue(0)
  })
```

Here we've told `Math.random()` to return 0, because 0 is under 0.5 and therefore will equate to stormy. Even if we lower our probability of stormy weather it will still be above 0, so 0 is a safe choice.

3. Now we've modified the behaviour of `Math.random()`, we can write our assertion. We want to `expect` `weather.isStormy()` *to be truthy*:

```js
  it('can be stormy', function () {
    spyOn(Math, 'random').and.returnValue(0)

    expect(weather.isStormy()).toBeTruthy()
  })
```

4. Run your tests. The first error in the stack trace should be `ReferenceError: Weather is not defined`. 

5. Create a `Weather.js` in your `src/` folder, and add a `Weather` constructor and prototype. Be sure to include the file into `SpecRunner.html` also, underneath your other source files.

6. Run your tests again. You should now have one error: `TypeError: weather.isStormy is not a function`. Add the `isStormy` method to your `Weather` prototype (leave it empty!). 

7. Run your tests again. Your error should now read: `Expected undefined to be truthy.`. Jasmine is now telling us our method is returning `undefined`. We want it to return a Boolean of `true` or `false`. Inside the `isStormy` method, add conditional logic that will return `true` if `Math.random()` is less than 0.5 or `false` otherwise:

```js
  isStormy: function () {
    if (Math.random() < 0.5) {
      return true
    } else {
      return false
    }
  }
```

8. Run your tests. You should be all green :green_heart:.

***
:bulb:

Comment out the `spyOn` call in your test and run your tests again, refreshing the page a few times. You should see the tests passing sometimes and failing other times. This is what would happen if we didn't override `Math.random()`.
***

## Red, green, REFACTOR

By now we've had plenty of reds, and a few comforting greens. What we haven't done yet (because we haven't needed to) is refactor our code. Refactor simply means to go back and make the code better - it could be by cutting down the amount of code to make it easier to read, or by doing it a different way that might offer increased performance. Either way, we can rest assured now that we can *fearlessly* change our code - if we break it then our test suite Jasmine will tell us. 

We're going to take the opportunity to refactor `isStormy`. 

1. Remove the entire code block (`{ ... }`) following the `if` statement, and remove the entire `else` block so you are left with:

```js
  if (Math.random() < 0.5)
```

2. Now change your `if` to `return`:

```js
  return (Math.random() < 0.5)
```

3. Run your tests. They should still be green.

***
:bulb:

The `(Math.random() < 0.5)` statement contains a comparison operator, so it doesn't matter if it is in an `if` statement or not - it will always evaluate to `true` or `false`. Therefore we can just `return` the statement.
***

4. There is still one small issue and that is that we have a *magic number*. A magic number is a number that doesn't mean anything to the person reading the code. In this case we know `0.5` is the probability of non-stormy weather, but anybody else looking at our code won't know this. Add a new property `NOT_STORMY_PROBABILITY` to your constructor, and assign it 0.5:

```js
function Weather () {
  this._NOT_STORMY_PROBABILITY = 0.5
} 
```

***
:bulb: 

Our property name `_NOT_STORMY_PROBABILITY` is all in uppercase here because it is a *constant*. When say it's a constant, we mean its value isn't to be changed after it's first set. JavaScript (prior to ES6) doesn't have proper constants yet, so we use the uppercase naming convention to make other developers aware they shouldn't reassign to these variables.
***

5. Now change your return value to reflect the change:

```js
  return (Math.random() < this._NOT_STORMY_PROBABILITY)
```

6. Run your tests again. Should still be green.

## Without the Walkthrough

Create a test `can be nice` that expects `isStormy` to be falsy.

## Add, commit and push.

:twisted_rightwards_arrows: **Driver and Navigator switch roles**

[Continue to Part 4](lesson1_page4.md)