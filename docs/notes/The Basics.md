---
id: mr1v7w28j0iqezha4nvfklm
title: The Basics
desc: ''
updated: 1712161960662
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
    let age;
    >>undefined - variable is created but no value is assigned to it

- assignment:
    age = 35;
- initialization: assignment for the first time
  - usually done at the same time as creation:
    let age = 35;
    >>undefined - the convention that the let statement has no value remains
    - check by calling the variable:
    age;
    >>35

### Constants

- keyword: const
    const PI = 3.14592653589793; - unlike variables, you have to assign constant value upon declaration
    >> undefined
    - use this constant to calculate circumference of a given circle:
    let diameter = 3; - create variable and assign value of three
    >>undefined - remember it will stick to the  convention...
    let circumference = diameter * PI; create variable and assign value of the const PI and the var diameter (compound expression including
    a constant, a variable, and an mathematical operator)
    >>undefined
    circumference - obtain the variable's value by calling it
    >>9.42477796076938

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

### Addition & Subtraction Assignment

### Multiplication & Division Assignment

## Strings

### Joining Strings

### Finding the Length of a String

### Getting a Character from a String

### Getting Multiple Characters from a String

### Trimming Whitespace from a String

### Other Useful String Methods

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
