# Fahrenheit to celsius converter

What we will be making
------
We will create a simple tool that takes a temperature from the user in Fahrenheit and converts it to Celsius. 

Preparation
------
In the command line, change directory into **~/Projects** and create a new directory called **fToC**.  Change directory into this folder, create an index.html file, save and populate the basic HTML structure (hint: `!` then `Tab`).

Getting started
------
To add JavaScript to the project, you just need to include `script` tags inside the `body` tags, setting the `type` attribute’s value to `text/javascript` to tell the browser to treat the enclosed contents as JavaScript:

```javascript
<script type="text/javascript">
	// JavaScript code goes here
</script>
```

Prompting the user
------
JavaScript has built in functions, which are reusable bits of code, which usually return a value after they’ve finished executing. Functions will be covered in more detail, but for now let’s call one of JavaScript’s predefined functions `prompt`:

```javascript
var fahrenheit = prompt('Please enter the temperature to convert in Fahrenheit:')
```

Save your **index.html** file and open it in the browser. You should see:

![Prompt](https://mcr.codes/wp-content/uploads/2017/06/Screen-Shot-2017-06-19-at-00.23.00.png)

***
:bulb:

You might be thinking: “What’s going on here?”. Well, essentially we are calling a function `prompt` and we pass it an argument ('Please enter the temperature to convert in Fahrenheit:'). `prompt` then takes this argument and tells the browser to pop up a prompt with the passed argument displayed as the prompt’s message. The user types in their answer. This answer is the return value of the prompt function. This return value then gets assigned to the myName variable.
***

:twisted_rightwards_arrows: **Switch driver/navigator roles**

The formula
------
We’ve asked the user for their temperature in Fahrenheit, and we’ve assigned their answer to the `fahrenheit` variable. Now we need to write a formula that takes this variable and uses it in an equation to work out the Celsius equivalent.

To convert Fahrenheit to Celsius, you need to take the Fahrenheit amount, subtract 32, multiply by 5 and then divide by 9. Let’s write this up in code, assigning our formula to a new variable `celsius`:

```javascript
var fahrenheit = prompt('Please enter the temperature to convert in Fahrenheit:')
var celsius = ((fahrenheit - 32) * 5) / 9
```

Your `fahrenheit` variable will equal the user’s input, and the `celsius` variable will now equal the `fahrenheit` variable converted to Celsius. 

***
:bulb:

Notice above how we’ve used brackets (in programming we usually say ‘parentheses’) in the mathematical equation. If you’ve ever used a scientific calculator then this syntax may be familiar. Any code inside parentheses will be evaluated before everything else. This is important as different mathematical operators in JavaScript have different precedence:

* P - parentheses
* E - exponentiation
* M - multiplication
* D - division
* A - addition
* S - subtraction

Without parentheses in our equation, it would look like this: `fahrenheit - 32 * 5 / 9`. As per PEMDAS, the `32 * 5` would happen first as the multiplication operator has highest precedence. Then the answer would be divided by `9` and lastly the `fahrenheit - answer` would take place, leading to the incorrect result of `72.2`. 

If Maths isn’t your thing and you are ever in doubt then always use parentheses to prioritise the order of calculation in your formulas.
***

Alerting the user
------
We have the converted value stored in our `celsius` variable. Now we just need to present it to the user:

```javascript
var fahrenheit = prompt('Please enter the temperature to convert in Fahrenheit:')
var celsius = ((fahrenheit - 32) * 5) / 9

alert('In celsius, that equals: ' + celsius + ' degrees')
```

***
:bulb:

`alert` is another built in JavaScript function. It’s very similar to `prompt` but it doesn’t take user input, and doesn’t have a return value.
***

***
:bulb:

You may have noticed that we’ve just used the `+` operator to add strings together. This is called string concetanation. JavaScript is clever enough to know that if the type of one of the values isn’t a number and the `+` operator is used then the two values should be appended together. If one of the values is a Number and the other a String then this is referred to as coercion (a.k.a converting types).
***

:twisted_rightwards_arrows: **Switch driver/navigator roles**

Handling edge cases
------
Edge cases are extreme scenarios we need to handle. By extreme, we mean we don’t want these scenarios to happen. For example, if you entered into the above prompt a String of text such as ‘hello’ and tried to execute the code then the alert would come back with: 

![Edge case example](https://mcr.codes/wp-content/uploads/2017/06/Screen-Shot-2017-06-19-at-01.27.38.png)

This isn’t the most informative thing for us to display to our user - how are they supposed to know what they’ve done wrong? Fortunately in JavaScript we can check if a value isn’t a number with `isNaN(string)`. `isNaN` takes a type and attempts to convert it to a Number. If it fails to convert the type then it returns a Boolean of `true` (the type is not and cannot be a Number), otherwise if it can convert the type to a Number it will return `true`. Let’s see how we can use `isNan` to handle edge cases in our application:

```javascript
var fahrenheit = prompt('Please enter the temperature to convert in Fahrenheit:')
var celsius = ((fahrenheit - 32) * 5) / 9

if (isNaN(celsius)) {
	alert('The converter only accepts Number values. Please refresh your page and try again.')
} else {
	alert('In celsius, that equals: ' + celsius + ' degrees')
}
```

Here we’ve just added conditional logic (if/else) to see if celsius is a Number or not. If a user enters a value for `fahrenheit` that isn’t a Number and this gets passed to the equation assigned to `celsius`, then `celsius` will equal the type of `NaN` (Not a Number) because you can’t do division and multiplication on the String type in JavaScript. 

Practise
------
If you have finished the above, then in your pairs follow the same principes to create a BMI (Body Mass Index) calculator. The formula for calculating BMI is:

`Body weight in kilograms divided by height in metres squared (a.k.a metres height x metres height).`

You will need two prompts for this: one that stores the user's weight, and another that stores the user's height.

***
:bulb:

Pair effectively! Remember, the driver should only be typing what the navigator tells them to type, and the two of you should be swapping regularly (no more than every 15 minutes or so) so that both of you have chance to drive and navigate. 

Don't feel as the driver that you have no input. If you disagree with what your navigator is telling you to do then explain your reasoning to them.

If, as a navigator, you are unsure of what to tell your driver to do, then ask your driver if they have an approach they would take and try to guide them off of that approach. Don't however allow the driver to start coding without your instruction.
***