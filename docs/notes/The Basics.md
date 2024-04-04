---
id: mr1v7w28j0iqezha4nvfklm
title: The Basics
desc: ''
updated: 1712251001624
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
let tribbles = 6; //initialize variable tribble with value of 20
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

## Template Literals

## Undefined & Null

## Booleans

### Logical Operators

### Comparison Operators

## Type Coercion

### Equality with Coercion

### Truthiness

### Uses for Truthiness
