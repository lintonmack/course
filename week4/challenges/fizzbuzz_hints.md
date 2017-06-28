FizzBuzz - with hints
------
The rules of FizzBuzz are simple: 

1) You pass FizzBuzz a number. 
2) If that number is divisible by 3, return "Fizz".
3) If that number is divisible by 5, return "Buzz".
4) If that number is neither divisible by 3 nor 5, return the number.
5) **The catch**: If that number is divisible by both 3 and 5, return "FizzBuzz".

```js
function fizzBuzz (number) {
  // your code here
}

console.log(fizzBuzz(3)) // 'Fizz'
console.log(fizzBuzz(5)) // 'Buzz'
console.log(fizzBuzz(15)) // 'FizzBuzz'
console.log(fizzBuzz(7)) // 7
```

Hints
------
* The best way to check if a number is divisible by another number in JavaScript would be to use the `%` arithmetic operator. [% on MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Remainder_()). Where the remainder is 0, the number is divisible (use [strict equality operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Identity_strict_equality_())).
* You will probably want to use conditional logic (a combination of `if`/`else if`/`else`).
* To check a number is divisible by both 3 and 5, you will need to use [logical AND](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators#Logical_AND_()) (`&&`).