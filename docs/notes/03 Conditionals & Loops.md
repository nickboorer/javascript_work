---
id: pd7aw62mfzygyjylgkd29os
title: 03 Conditionals & Loops
desc: ''
updated: 1712677169789
created: 1712598672389
---
Adding logic and structure to programs:

- "Control Structures"

## Making Decisions with Conditionals

- run blocks of code when a condition is true
  - warning message
  - lose a life
- generally use comparison operators (===, >, <, >=, <=)
  - can combine with logical operators
- overall statement must evaluate to true or false

### if Statements

- runs if some condition is true
- e.g., log a message to the console if value greater than specified threshold:

```js
let speed = 30; //initialize speed at 30kmh
    console.log(`Your current speed is ${speed} kmh.`); //prints the current speed to the console
    if (speed > 25) { //sets the condition (faster than 25 kmh)
    console.log("Slow down!"); //prints out the warning message if the speed exceeds 25kmh
    }
//Your curren speed is 30 kmh.
//Slow down! - the condition passed (30 is greater than 25) so the warning message was printed
```

- two main parts:
  - _condition_ - written inside parentheses: if (speed > 25)
  - _body_ - code to be run if condition is true: {console.log("Slow down!");}

### if...else Statements

- when you want to run one piece of code if condition is true, and another piece of code if condition is false

```js
let speed = 20;
console.log(`Your current speed is ${speed} kmh.`);
if (speed > 25) {
console.log("Slow down!"); // this prints if the speed exceeds 25 kmh
} else { //otherwise...
console.log("You're obeying the speed limit."); //...this prints
}
```

- this statement has two bodies, each enclosed within its own set of braces
  - the first runs if the condition is true
  - the second runs if the condition is false
    - in the case the second condition runs because speed is less than 25 kmh

### More Complex Conditions

- incorporate logical operators to make more complex conditions:

```js
if (speed > 25 && hour > 7 && hour < 16>) {/*BODY*/} // here the condition is true if the speed is greater than 25 and it is after 7am and before 4pm
```

- but better to lump the school hours together in their own variable:

```js
let schoolHours = hour > 7 && hour < 16;
if (speed > 25 && schoolHours) {/*BODY*/} //if speed is faster than 25 and schoolHours is true (i.e., the time is currently between those limits)
```

### Chained if...else Statements

- need to decide between three or more possible branches
- chain multiple if...else statements:

```js
let speed = 20;
console.log(`Your current speed is ${speed}.`);
if (speed > 25) {
    console.log("Slow down");
} else if (speed > 15) {
    console.log("You're driving at a good speed.");
} else {
    console.log("You're driving too slowly!");
}
```

- Very similar to if...else statement above but now three sections:
  - if - speed is faster than 25
  - else if - speed is greater than 15 (but less than 26)
  - else - if speed is slower than 16
- Only _one_ body will be run - the first one whose condition evaluates to true
  - first it checks whether the speed is faster than 25
    - if so, it prints the first warning and stops
  - if not, it checks whether the speed is faster than 15
    - if so, it prints the encouraging statement and stops
  - if not, it tells you that you are driving too slowly.

### Braces

- you don't actually _need_ braces if the body consists of a single statement:

```js
if (speed > 25)
    console.log("Slow down!");
else
    console.log("You're driving under the speed limit.");
```

- each body contains only one statement so no braces are needed
- the bodies are split out onto separate lines for readability only - they could all be on the same line:

```js
if (speed > 25) console.log("Slow down!");
else console.log("You're driving under the speed limit.");
```

- but if there is more than one line in the body, then braces will be needed to specify where body ends and code begins

## Repeating Code with Loops

- run the same code as many times as needed
  - e.g., print out items on a shopping list
- keep running the code until condition is satisfied:
  - e.g., keeping on asking user to enter DOB until they get the correct format
- four kinds of loops:
  - while
  - for
  - for...in
  - for...of

### while Loops

- depends on conditional test
    - will not run at all if the condition is false at the start
- will keep running body as long as condition is true
    - this means it will run for as long as needed
        - you don't need to know how long that is at the start - the condition will determine this

```js
let speed = 30; //sets current speed 
while (speed > 25) { //set condition for body to run: speed is faster than 25 kmh
    console.log(`Your current speed is ${speed} kmh.`); //prints out current speed
    speed--; //reduces current speed by 1kmh and checks the condition again. If speed still faster than 25 kmh, it runs the body again
}
console.log(`Now your speed is ${speed} kmh.`); //once the speed reaches 25 kmg, the body stops running and this message is printed:
//Your current speed is 30 kmh.
//Your current speed is 29 kmh.
//Your current speed is 28 kmh.
//Your current speed is 27 kmh.
//Your current speed is 26 kmh.
//Now your speed is 25 kmh.
```

- **Beware of Infinite Loops**
    - condition is always true to loop never ends
        - e.g., in code above if "speed--" was changed to "speed++"
    - always ensure that the condition will eventually be false

### for Loops

- keeps running as long as condition is true
    - but code for managing repetitions is at the start of the loop and separate from the body
- commonly a looping variable keeping track of state of loop
    - set start value, update each time loop runs, and check a condition against that variable to determine when to stop


### for...of Loops


### for...in Loops