---
id: 421r4tvr6v807jic7phb1gu
title: 04 Functions
desc: ''
updated: 1712859909487
created: 1712682304276
---

A self-contained block of code for performing a certain task

## Declaring and Calling Functions

- Function declaration
  - four parts:
    - **function** keyword
    - name of function
    - (comma-separated list of parameters inside parentheses)
    - {function body, surrounded by braces}

```js
function sayHello(name) { // function name = sayHello, parameter = name, function body open brace
    console.log(`Hello, ${name}!`) //function body - prints "Hello, 'name'! to the console
} //function body closed

sayHello("Nick"); //"Nick" is the value for the parameter - the _argument_
//Hello, Nick!
//undefined - we haven't explicitly given the function a return value
sayHello("Mei");
//Hello, Mei!
//undefined
```

- The value passed for the parameter is called an _argument_, specified in parentheses when function is called
  - difference between parameter and argument:
    - _parameter_ = generic name for a function's inputs (only one set for any function)
    - _arguments_ = the actual input values passed to the function (a new set every time the function is called)

### Return Values

- Function above returned undefined because we haven't supplied a return value
- _Return value_ = the result of the processes carried out on the parameter inputs:

```js
function add(x,y) { //function called 'add' that takes two parameters
    return x + y; //keyword 'return' followed by an expression
}
```

- JavaScript will evaluate the expression and return the result:

```js
add(1, 2);
//3
```

- Important difference between a return value and text logged to the console
  - a value logged to the console _only_ exists in the log - cannot be used anywhere else
  - a return value is available for use elsewhere in the code
    - printing a return value to the console is just to help us see what is going on - no practical importance

- Can use a return value by calling the function in an assignment expression
  - return value then stored as a variable that we can use later:

```js
let sum = add(500, 500); //use the add function to sum 500 and 500 and assign the return value to the variable sum
//undefined
`I walked ${sum} miles`; //use the sum variable created above as a template literal
//I walked 1000 miles
```

- Could not do this with our sayHello function
  - it has no return value - it only prints to the console

- Not necessary to store return value in a variable to be able to use it again
  - use the function call itself anywhere a value can be used:

```js
`I walked ${add(500, 500)} miles`; // calling the function directly within the template literal
//I walked 1000 miles - return value inserted directly
```

- sayHello refactored to give a return value

```js
function sayHello(name) {
    return `Hello, ${name}!`;
}
sayHello("Nick").toUpperCase(); //applying a string method to the return value
//HELLO, NICK!
```

### Parameter Types

- data types of function parameters are not fixed
  - JavaScript is a _dynamically typed_ language
    - types of variables and parameters can change on the fly
  - c.f. statically typed languages - Go, C, Rust
    - variable and parameter types defined before programme is run

```js
add("Hello, ", "world!"); //pass two strings to the function
//'Hello, World! - add concatenates the strings

add(true, false);
//1 - booleans automatically coerced to numbers (1, 0) and summed

add(1, '1');
//'11' - adding a number and a string causes number to be coerced to a string, so here they are concatenated rather than summed
```

- Dynamic typing is very flexible
  - but can cause confusing bugs if you're not careful
    - Need to make sure you understand what types you are passing to your functions so that they e.g., sum rather than concatenate

### Side Effects

- Anything that a function does that makes a difference outside of the function
  - intended or unintended, e.g.:
    - updating value of a variable declared outside of the function
    - modifying an array or object
    - outputting a string to the console
- Not all functions have side-effects
- Some ONLY have side effects (e.g., our first version of sayHello, which had no return value)
  - Some have both return values and side-effects:

```js
let addCalls = 0; //declare variable 'addCalls' to keep track of how often the add function is called

function add(x, y) { 
    addCalls++; //increments addCalls each time the function runs
    console.log(`x was ${x} and y was ${y}`); //logs values of parameters to the console - a side effect
    return x + y; //returns sum of the parameters
}

//test:
let sum = add(Math.PI, Math.E);
//x was 3.141592653589793 and y was 2.718281828459045
addCalls;
//1
sum;
//5.859874482048838
```

## Passing a Function as an Argument

- Functions are _first-class citizens_:
  - can be used like any other value (number, string etc)
    - can be:
      - stored in a variable
      - passed to another function as an argument - often called a _callback_
        - the function its passed to "calls back" the function by executing it
        - we only use the function name - not the parentheses for the parameters
          - _refers_ to the function rather than _calling_ it:

```js
function sayHi() {
    console.log("Hi!"); //define function with no arguments that only calls console.log()

}
setTimeout(sayHi, 2000); //call built-in setTimeout function, passing sayHi as first argument and setting it to wait 2 seconds (2000ms)
//1 - immediately returns timeout ID (unique identifier for this call of the setTimeout function), then waits two seconds...
//Hi! ...and prints this to the console
```

## Other Function Syntaxes

- Function declarations (as above) similar to other languages (e.g. Python, C++)
  - Suitable for functions being called directly
  - not so great when being passed to other functions

### Function Expressions

- aka _function literal_
- _code literal_ whose value is a function
  - an expression that evaluates to a function
- two main differences from a function expression:
  - name is not needed (_anonymous function_)
  - cannot be written at start of line
    - must be some other code first
- can define a function expression and assign to variable in a single statement:

```js
let addExpression = function (x,y) { //anonymous 'function' is to right of assignment statement so treated as function expression
    return x + y;
}; //note that we now need a semi-colon after the final brace - this is actually the end of the assignment statement, not just the end of the function!
```

- Although this function is anonymous, it is now bound to a variable name and we can call it by calling the variable and passing the necessary arguments in parenthese:

```js
addExpression(1, 2);
//3
```

- More concise than defined function when passing to other functions

```js
setTimeout(function () { //defines anonymous function equivalent to sayHi function above 
    console.log("Hi!");
}, 2000); //closing brace followed by comma as it is an argument of the setTimeout function
//2
//'Hi!'
```

#### Named Function Expressions

- Optional function names in function expression:

```js
let addExpressionNamed = function add(x, y) {
    return x + y;
};
```

- the function name 'add' is not within function scope at all
  - so we cannot call it by using its name
- the function is still bound to the variable name as above
  - so we call it by using the variable name
- Not as common as anonymous functions
- Useful for debugging

### Arrow Functions

- _arrow function expressions_
  - used anywhere a function expression would work
    - but more compact
      - no 'function' keyword
        - argument list in parentheses followed by arrow (=>) and function body

```js
let addArrow = (x, y) => { //assigned to addArrow variable
    return x + y;
};

addArrow(10, 23); //called by using the variable name as with the function expressions above
//33
```

- can make this even more consise by using _concise body_ syntax
  - body on same line as rest of statement, so no braces
  - 'return' keyword is implied:

```js
let addArrowConcise = (x, y) => x + y;
```

- great for simple functions
  - cannot be used for function bodies made up of multiple statements
    - braces needed and 'return' must be explicitly stated if needed

- If only one parameter, further simplification possible
  - no parentheses needed
  - works for block body and concise body syntax

- Arrow functions are an efficient way to pass functions as arguments for other functions:

```js
setInterval(() => {
    console.log("Beep");
}, 1000);
```

```js
let squared = x => x * x;
squared(3);
//9
```

## Rest Parameters

- May need function to accept variable number of arguments
  - don't know in advance how many arguments will be passed to the function
- use a _rest parameter_
  - collect variable number of arguments into an array
- work with all types of function declarations

```js
let myColors = (name, ...favoriteColors) => { //function declared as an arrow function
    let colorString = favoriteColors.join(", "); //initialize variable colorString that joins all of the colors supplied to the argument with a comma separator
    console.log(`My name is ${name} and my favourite colors are ${colorString}.`); //print the template literal to the console
};
myColors("Nick", "blue", "green", "orange");
//My name is Nick and my favourite colors are blue, green, orange.
```

## Higher-Order Functions

- _higher order functions_ take another function as an argument
  - or output another function as return value
    - e.g., setTimeout() and setInterval()

### Array Methods that Take Callbacks

#### Finding an Array Element

- **arr.find()** - finds first element in array that matches criterion
  - criterion specified by callback function returning a Boolean:

```js
let shoppingList = ["Milk", "Sugar", "Bananas", "Ice Cream"]; //initializes a variable containing an array of shopping items
shoppingList.find(item => item.length > 6); //searches for first item in the list with more than 6 characters using callback arrow function in concise body syntax (only one statement) - no braces and no return needed
//bananas (7 characters)

shoppingList.find(item => item[0] === 'A');
//undefined - there is no item in the list that starts with 'A'
```

#### Filtering the Elements of an Array

- **arr.filter()** - returns a new array containing all items in original array that satisfy the criterion

```js
let shoppingList = ["Milk", "Sugar", "Bananas", "Ice Cream"]; //initializes a variable containing an array of shopping items
shoppingList.filter(item => item.length > 6);
//(2) ['Bananas', 'Ice Cream']
```

#### Transforming Each Element of an Array

- **arr.map()** - applies a function to each item in the array and stores the results in a new array
  - preferable to a loop for this kind of operation:
    - concision
    - _self-documenting_ - you know exactly what is happening with the map method - no need for further documentation
  - a loop would be better for more specialised needs
    - e.g., num of elements in output array doesn't match number in original array

```js
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let cubes = numbers.map(x => x * x * x);
cubes;
//(10) [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

- also useful to extract same piece of information from each item in an array of similar items:
  - e.g., array of items, each with a name and price property
    - you want to get an array of just the prices:

```js
let stockList = [
    {name: "Cheese", price: 3 },
    {name: "Bread", price: 1 },
    {name: "Butter", price: 5 },
];
let prices = stockList.map(item => item.price);
prices;
//(3) [3, 1, 5]
```

### Custom Functions that Take Callbacks

- simply include name for the callback in the function's list of parameters (just like name for any other parameter)
  - then add parentheses after this name when calling this function in the function body:

```js
function doubler(callback) { //define function with callback parameter
    callback(); //2 * callback (adding parentheses because we are calling the parameter as a function)
    callback();
}

doubler(() => console.log("Hi there!")); //pass a function as the callback parameter
```

- can also create a higher-order function whose callback takes arguments:

```js
function callMultipleTimes(times, callback) { //callMultipleTimes has two parameters - a number and a function
    for (let i=0; i < times; i++) { //function body is a for loop calling callback(i), passing looping variable as argument to callback
        callback(i);
    }
}
callMultipleTimes(10, time => console.log(`This time was time: ${time +1 }`)); //callback takes a single argument - arrow function incorporating time into message logged to console
```

### Functions that Return Functions

- Higher-order functions can also output functions as return values:
  - e.g., creating various functions to add suffixes to end of string - '!!!', '???'
    - don't want to manually define separate function for each possible suffix, or pass text and suffix as parameters each time you call it
      - define higher-order function that takes a suffix as an argument and returns a function to append it to a string:

```js
function makeAppender(suffix) {
    return function (text) { //first return keyword used by makeAppender to return anonymous function
        return text + suffix; //second return keyword inside anonymous function. When anon called, returns value of anon function's text parameter + makeAppender's suffix parameter
    };
}

let exciting = makeAppender("!!!"); //first call outer (makeAppender) function to access...
exciting("Hello"); //...inner function (now bound to variable 'exciting' and called as a function by adding parentheses and argument)
//'Hello!!!'
```

- We can now generate additional functions for other suffixes without needing to rewrite the makeAppender function
  - each function remembers value of suffix passed to makeAppender()
    - defined within makAppender()'s scope
      - would normally disappear once makeAppender had executed - but not the case here
        - because we retain a reference to the inner function of makeAppender by means of the variables we have created
          - functions like this are known as _closures_:
            - they close over their environments like a dome that preserves all the variables in the inner scope

```js
let puzzling = makeAppender("???");
let winking = makeAppender(" ;-)");
```
