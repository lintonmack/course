Egg timer - with hints
------
Given a number of seconds, eggTimer will count down from that number to 0, each time console logging `n seconds to go` where n is the number remaining. If only one second is remaining then you should log `1 second to go`. When 0 is reached, you should log `Dinner is ready!`. This doesn't have to be representative of real time!!! (i.e. if you pass 10 seconds, the function shouldn't need 10 seconds to run).

```js
function eggTimer (seconds) {
  // Your code goes inside here, with the below console.log calls in the correct places
  console.log('n seconds to go')
  console.log('1 second to go')
  console.log('Dinner is ready!')
}

eggTimer(10)
// 10 seconds to go
// 9 seconds to go
// 8 seconds to go
// 7 seconds to go
// 6 seconds to go
// 5 seconds to go
// 4 seconds to go
// 3 seconds to go
// 2 seconds to go
// 1 second to go
// Dinner is ready!
```

Hints
------
* The best way to approach this would be to use a `for` loop: define a counter variable with a value equal to the number of `seconds` passed into the function; set the condition in which the loop should keep running to be that the counter variable isn't less than 0; and set the code to execute after each iteration to decrement (`--`) the counter variable.
* Inside the `for` block, use conditional logic (`if`, `else if` and `else`) to decide what to `console.log`.