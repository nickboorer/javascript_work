---
id: mr1v7w28j0iqezha4nvfklm
title: 01 The Basics
desc: ''
updated: 1712328707068
created: 1712154758094
---

## Expressions & Statements

- Expression: fragment representing a single value
  - evaluation: determining the value of an expression
  - Compound expression: composed of two or more expressions (such as when using operators)
  - literal: direct representation of fixed value
    - number literal: a number in code
  - operator: symbol to manipulate expressions
- Statement: complete "sentence" - an instruction for the computer
  - e.g. alert("Hello World!");
    - instructs browser to display a dialogue box with the message "Hello World"
  - Expression -> statement: semi-colon at the end

## Numbers & Operators

- mathematical operators: + - * /

### Order of Operations

- PEMDAS - if in doubt, use parentheses

### Floating Point

- limited precision
  - a problem when working with money calculations
    - convert to cents/pence before calculating and then convert back to pounds/dollars/euros etc
- truncated if too long

## Bindings

- A box with a label
  - variables allow you to change or update what is in the box
  - constants remain them same

### Variables

- keywords: var or let (preferred nowadays)
e.g.:

```javascript
    let age;
    >>undefined //variable is created but no value is assigned to it
```

- assignment:

```javascript
    age = 35;
```

- initialization: assignment for the first time
  - usually done at the same time as creation:

```javascript
    let age = 35;
    >>undefined //the convention that the let statement has no value remains
    //check by calling the variable:
    age;
    >>35
```

### Constants

- keyword: const

```javascript
    const PI = 3.14592653589793; //unlike variables, you have to assign constant value upon declaration
    >> undefined
```

- use this constant to calculate circumference of a given circle:

```javascript
    let diameter = 3; 
    //create variable and assign value of three
    >>undefined //remember it will stick to the  convention...
    
    let circumference = diameter * PI; 
    /*create variable and assign value of the const PI and the var diameter (compound expression including
    a constant, a variable, and an mathematical operator)*/
    >>undefined
    circumference 
    //obtain the variable's value by calling it
    >>9.42477796076938
```

### Naming Conventions

- descriptive names - clear what they represent
- case sensitive: ID != id or Id or iD

### Variable Names

- convention is camel case
- snake case as an alternative (slightly clearer but much harder to type)

### Constant Names

- True constants (will never change whenever the program runs - eg. PI, hours in a day etc)
  - All caps snake case: PI, HOURS_IN_A_DAY
- Otherwise same convention as variables

## Incrementing & Decrementing

a. initialize and then change to value + 1 on each increment
    it first calculates expression to right of assignment operator (=)
    then it updates value on left of operator

```js
    let money = 100; //declare variable and initialize at 100
    money = money + 1; //assign new value by taking previous value of 100 and adding 1
```

b. increment operator "++"
    increases value of variable to which it is attached by 1
    no need for full assignment expression:
    works also to decrement with "--"
    Can be applied before or after the variable

- Prefix incrementing/decrementing:

```javascript
    let temperature = 70;
    ++temperature; //adds one to temperature - output: 71
    ++temperature; //adds one to new temperature - output: 72
    --temperature; //subtracts one from new temperature - output 71
```

- Postfix incrementing/decrementing:

```js
let books = 2; //initialize variable books to 2
books++; //add one to books
books; //evaluate books: 3
books--; //subtract one from books
books; //evaluate books again: 2
```

### Addition & Subtraction Assignment

- "++" and "--" only increment or decrement by one
  - to increment by other values use addition or subtraction assignment operators "+=" and "-=":

```js
let cookies = 12; //initialize variable cookies with value of 12
cookies -= 5; //subtract 5 from initial value of cookies
cookies; //evaluate new cookies - output: 7
```

```js
let price = 20; //initialize variable price at 20
price += 5; //add 5 to initial value of price
price; //evaluate new price - output: 25
```

### Multiplication & Division Assignment

- The same idea works with multiplication and division:

```js
let tribbles = 6; //initialize variable tribbles with value of 20
tribbles *=2; //set new value by multiplying initial value by 2
tribbles; //evaluate new value: 12
tribbles /=3; //set new value by dividing value of 12 by 3;
tribbles; //evaluate new value: 4
```

## Strings

- represents text
  - a "string" of characters
- string literal = direct representation of the string value
  - surround text with "" or ''
  - can also include punctuation, spaces, numerals
    - but remember that numerals in a string cannot be evaluated as numbers

```js
let greeting = "Hello!"; //initializes and assigns string literal value "Hello!' to variable greeting
greeting; //evaluates greeting: 'Hello!'
```

### Joining Strings

- "+" operator joins strings
  - can build up longer messages from several strings:

```js
let first = "First string"; //initializes variable first and assigns string literal as value
let second = "Second string"; //initializes variable second and assigns string literal as value
let joined = first + second; //initializes variable joined made up of values of first and second joined together
joined; //evaluates joined: 'First stringSecond string'
```

- note that no space is added automatically - you need to make sure you do that yourself:

```js
let joined = first + " " + second; //initializes the variable and sets its value with a space between the two other variables 
joined; //evaluates joined: 'First string Second String'
```

### Finding the Length of a String

- add '.length' to the string or the variable containing it
  - counts all characters including spaces and punctuation

```js
"abc".length; //evaluates to 3
let longString = "This is my very long string"; //initializes variable longString and sets its value to a string literal
longString.length; //calculates the length of the value stored in longString: 27
```

### Getting a Character from a String

- use characters index to get a specific character from a string
- JavaScript uses zero-based indexing so first character is at position 0

```js
let alphabet = "ABCDEFG";
alphabet[0]; //returns 'A'
alphabet[1]; //returns 'B'
alphabet[10] //returns undefined because it is beyond the length of the string
```

### Getting Multiple Characters from a String

- a slice using the ".slice()" method
  - method is a function attached to a particular value or datatype
    - used to perform a calculation on the object they're attached to
    - object.method(arguments)
- .slice() takes 2 arguments: start index (inclusive) and end index (exclusive)
  - (indexing works in the same way as Python)

```js
let sentence = "My name is Nick.";
sentence.slice(3, 7); //evaluates to 'name' (includes the character at position 3 'n' but doesn't include the character at position 7 ' ') 
```

### Trimming Whitespace from a String

- whitespace = e.g. spaces & tabs - not printed characters
- spaces at beginning and end of string removed with ".trim()" method
  - doesn't touch spaces between words

```js
let inputText = " Here is my input   "; //variable containing a string literal with extraneous spaces at beginning and end
inputText.trim(); //removes the spaces at start and end. Evaluates to a NEW string: 'Here is my input'
inputText; //still evaluates to ' Here is my input   ' because the variable hasn't been updated
```

### Other Useful String Methods

- str.toLowerCase() - returns a new string with all upper case letters converted to lower case
- str.includes(otherStr) - returns true if str includes the string used as the argument
- str.padStart(num, char) - returns a new string with at least num characters and adds as many char as necessary if not already num in length
- str.repeat(count) - returns a new string with str repeated count times

## Escape Sequences

- may need special characters in a string:
  - line breaks
  - tabs
- include these by using break characters:
  - always start with a backslash:
    - "\n" - new line

```js
let hello = "Hello\nWorld";
console.log(hello)
/*output:
Hello
World*/
```

Other escape sequences:

- \' - Single quote
- /" - Double quote
- \\ - Backslash
- \n - New line
- \t - Tab

```js
console.log("This string has \"double quotes\" and a \\ backslash character");
//output: This string has "double quotes" and a \ backslash character
```

You don't need to escape single quotes in a string inside double quotes and likewise for double quotes in a string inside single quotes

## Template Literals

- Special string that evaluates the expression inside it
  - allows dynamic string values
- contained within backticks (`) (not quotation marks)
- use placeholder syntax: ${}
  - text inside the braces is treated as an expression
    - evaluated before the final string is evaluated

```js
let name = "Nick";
`Hello, ${name}!`;
//output 'Hello, Nick'

name = 'Dolly';
`Hello, ${name}!`;
//output: 'Hello Dolly!
```

- Any expression can be included between the braces:

```js
`There are ${60*60*24} seconds in a day`;
//output: 'There are 86400 seconds in a day'
```

- Useful for:
  - taking input and inserting into the string
  - building a string from several variables:

```js
let noun = "moon";
let adverb = "strangely";
let adjective = "red";
//without template literals:
"The " + noun + "was " + adverb + adjective + ".";
// 'The moon was strangely red.'
`The ${noun} was ${adverb} ${adjective}.`;
// 'The moon was strangely red.'
```

- template literals make it much easier to read and understand that custom values are being inserted.

## Undefined & Null

- values 'undefined' and 'null' represent 'nothing

- JS has no value for something: 'undefined':

```js
let nothing;
nothing;
//undefined (we have assigned no value to the variable 'nothing')
```

- also returned when a function has no useful value to return in the console:

```js
alert("I have no value");
//undefined (although the function creates a pop up alert, there is no value it can return in the console)
```

- 'null' is used when programmers explicitly mark something as empty or having no value:

```js
let address = null;
address;
//null
```

- no functional difference but makes intentions clear - deliberately stating that it is an empty value rather than something you haven't defined yet

## Booleans

- True or false
  - a way to talk about logic - enabling programme to behave differently in different conditions
  - supported by logical operators and comparison operators

### Logical Operators

- and: && - returns true only if both operands are true
- or: || - returns true if either operand is true
- not: ! - only takes one operand and reverses its value

```js
let powerup = true;
let jumping = true;
powerup && jumping;
//true - because both of the operands are set to true
```

```js
jumping = false;
powerup && jumping;
//false - because one of the operands (jumping) ias now false
```

```js
let hitByFireball = false;
let touchedMonster = true;
hitByFireball || touchedMonster;
//true - because one of the operands (touchedMonster) is true
```

```js
let alive = false;
!alive;
//true - because the ! returns the inverse of the operand it is attached to
```

```js
let carryingBox = true;
let swimming = false;
!carryingBox && !swimming;
//false - not swimming but carrying box so one of the conditions - to not be carrying a box - is not fulfilled
```

- the final expression evaluates as follows:
  - !true && !false
  - false && true
    - one of the value is false, so the && returns false

- useful trick:

```js
!a && !b; //not a and not b
//can be rewritten as:
!(a || b); //not (a or b) - the part in the parentheses evaluates first
!(a && b); //not (a and b) instead of;
!a || b; //not a or not b
```

### Comparison Operators

- return true or false based on result of comparison

- === - checks whether two values are equal; returns true if they are, false if they aren't
- !== - checks whether two values are NOT equal; returns true if they aren't, false if they are

```js
5 === 5; //true
6 === 7; //false
2 + 2 === 4; //true
"hello" === "goodbye"; //false
"hello" === "hel" + "lo"; //true
false === false; //true
true === false; //false
```

```js
let answer = 2 + 2;
answer === 5; //false
answer === 4; //true
```

```js
8 !== 8; //false
"apples" !== "oranges"; //true
// same as:
!(8 === 8) //false
!("apples" === "oranges") //true
```

- > greater than
- < less than
- => greater than or equal to
- <= less than or equal to

```js
1 > -1; //true
10 > 10; //false
10 >= 10; //true
-1 < 1; //true
10 < 10; //false
10 <= 10; //true
```

- when comparing strings this is basically done alphabetically and stops as soon as a difference is found:

```js
"cat" < "dog"; //true - because cat would appear before dog in a dictionary
"abc" > "abbcdef" /*true - the third letter c in the first string is after the third letter b in the second string 
- length is irrelevant here because the comparison has already stopped at the third character*/
```

## Type Coercion

- automatic conversion of value from one data type to another
  - where different data types appear in the same expression and can't be evaluated
  - e.g. string + number

```js
"Current score: " + 10; //JavaScript coerces the 10 to a string and then concatenates
//'Current score: 10' (a string can't be coerced to a number - it would be senseless)
```

- booleans coerced to numbers (true = 1, false = 0):

```js
100 + true;
//101
```

### Equality with Coercion

- == double equals (rather than the triple equals above)
  - applies coercion to the operands

```js
0 == false; //coerces the Boolean to a number (0 === 0)
//true
0 === false; //Boolean not coerced so no equality
//false
```

- what will be coerced can be hard to guess:

```js
"1" == 1; //true - string of a number is coerced to equivalent number 
undefined == null; //true
undefined == false; //false
"" == 0; //true
"" == false; //true
```

- != - opposite of ==
  - determines whether the operands are not equal after coercion:

```js
0 !== false;
//true -  without coercion, 0 is not equal to false
0 != false;
//false - after coercion of he boolean to 0, the statement that 0 is not equal to 0 is false
```

- the unpredictability of using the coercive operators means they should be avoided if possible

### Truthiness

- defines how non-Booleans can be treated as Booleans
  - allowing use of logical operators with any type of value
- truthy - equivalent to true: all non-zero numbers and non-empty strings
- falsy - equivalent to false: undefined, null, 0, and empty strings

- check truthiness with two not operators: !! (not not)
  - ! always returns a Boolean, whatever the data type

```js
!0 // ! coerces the 0 to a Boolean (false) and inverts it
//true
!!0 // the second ! inverts the Boolean again (false), giving the Boolean of the original value
!!1;
//true - non-zero number
!!"hi";
//true - non-empty string
!!"";
//false - empty string
!!undefined;
//false
!!null;
//false
```

- && and || applied to non-Booleans don't return a Boolean
  - return one of the original operands
- &&:
  - if first operand truthy, second operand returned
  - if first operand falsy, first operand returned
- ||:
  - if first operand truthy, first operand returned
  - if first operand falsy, second operand returned

```js
15 && 17;
//17
0 && 20;
//0
undefined && null;
//undefined
"" || "hello"; //first operand falsy (empty string) so second operand returned
//'hello'
"hello" || "goodbye" //first operand truthy (non-empty string) so first operand returned
//'hello'
```

### Uses for Truthiness

- providing a default value to a variable if non supplied (maybe a missed entry on a form):

```js
let name;
name = name || "No name provided"; //name is falsy
name; //second operand returned as default
//'No name provided'
```

- && to short circuit an expression - to decide whether or not to run some code:

```js
let score = 0;
score && alert(`Your score is ${score}!`); //if the score is zero, then the alert is not evaluated at all
0 //no alert is displayed
//score goes up:
++score;
//1 - added one to the score
score && alert(`Your score is ${score}!`); //score is now truthy so the second operand is evaluated
//undefined (there is no useable console value returned from the expression) 
//alert displayed in a dialogue box saying "This page says Your score is 1!
```
