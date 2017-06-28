Egg timer
------
Given a number of seconds, eggTimer will count down from that number to 0, each time console logging `n seconds to go` where n is the number remaining. If only one second is remaining then you should log `1 second to go`. When 0 is reached, you should log `Dinner is ready!`. This doesn't have to be representative of real time!!! (i.e. if you pass 10 seconds, the function shouldn't need 10 seconds to run).

```js
function eggTimer (seconds) {
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

***
:bulb:

If you have finished the above and really want to challenge yourself, then use [setInterval](https://www.w3schools.com/jsref/met_win_setinterval.asp) to count down in actual time.
***

Stuck? [See hints](https://github.com/MCRcodes/course/blob/master/week4/challenges/egg_timer_hints.md).