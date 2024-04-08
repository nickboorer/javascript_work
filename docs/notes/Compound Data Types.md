---
id: cilhezepe7hpjdmd0cafetj
title: Compound Data Types
desc: ''
updated: 1712591561286
created: 1712329155586
---

Arrays and Objects

## Arrays

- Holds an ordered list of values
- Elements can be any data type
  - don't have to all be the same data type
- Collect related values in a single place
- Can add and remove values

### Creation & Indexing

- List elements, separated by comma, inside square brackets:

```js
let primes = [2, 3, 5, 7, 11, 13, 17, 19];
primes;
//(8) [2, 3, 5, 7, 11, 13, 17, 19] 
//(length of array) [elements]
```

- Arrays are zero-indexed
- Each element has an index number, starting from [0]
- access elements with "name of array[index]:

```js
primes[0];
//2 - the first element of the primes array at position 0
```

- Final element is always at position: [length of array - 1]
  - because of zero-indexing
- If length is not known, use dot-notation to get length property

```js
primes.length;
//8 - length of the arrays
primes[7]; //subtract one from the length to get the final position
//19 - final element
```

- This can be more effectively done in a single statement:

```js
primes[primes.length-1];
//19
```

- index outside of array range returns "undefined":

```js
primes[10]
//undefined (there are only 8 values so the highest possible index is [7])
```

- You can use the indexing syntax to replace an element inside the array:

```js
primes[2] = 1;
primes;
//(8) [2, 3, 1, 7, 11, 13, 17, 19]
// there is now a 1 at the third position (index[2]) of the array instead of the original 5
```

### Arrays of Arrays

- Can contain other arrays
  - multi-dimensional arrays, e.g.:
    - two-dimensional grids of points;
    - tables

```js
let ticTacToe = [
    ["", "", ""],
    ["", "", ""],
    ["", "", ""]
];
//outer array with three elements - each an array (inner arrays)
//each inner array contains three empty string - squares of noughts & crosses grid
//each inner array on a new line for readability only - could easily be written all on one line
ticTacToe;
//(3) [Array(3),Array(3),Array(3)]
//(length of outer array), [inner arrays(length)]
//drill down:
/*
0: (3) ['', '', '']
1: (3) ['', '', '']
2: (3) ['', '', '']
length: 3
[[Prototype]]: Array(0)
*/
```

- Noughts & Crosses board currently empty
  - add X in top-right corner
- access first row ticTacToe[0]
- access third element of that row: ticTacToe[0][2]

```js
ticTacToe[0][2] = "X";
/*
0: (3) ['', '', 'X']
1: (3) ['', '', '']
2: (3) ['', '', '']
The X has now appeared in the top right
*/
```

### Array Methods

- modify arrays: "mutation'
  - adding elements
  - deleting elements
  - changing order
- creating new arrays while leaving originals untouched
- important to know whether the method will mutate the array

#### Adding and Element to an Array

- .push(element) method:
  - adds element to end of array:

```js
let languages = []; //initialize variable as empty array
languages.push("Python");
//1 - now one element in the array
languages.push("Haskell");
//2 - two elements
languages.push("JavaScript");
//3 - three elements
languages.push("Rust");
//4 - four elements
languages; //call the array
//(4) ['Python', 'Haskell', 'Javascript', 'Rust']
```

- .unshift(element) method:
  - adds element to the beginning of an array:

```js
languages.unshift("Erlang");
//5
languages.unshift("C");
//6
languages.unshift("Fortran");
//7
languages;
//(7) ['Fortran', 'C', 'Erlang', 'Python', 'Haskell', 'Javascript', 'Rust']
//The newly added languages are all now at the beginning of the array
```

#### Removing Elements from an Array

- .pop() method:
  - removes the last element in the array:

```js
languages.pop();
//'Rust' - returns the value of the element being removed
languages;
//(6) ['Fortran', 'C', 'Erlang', 'Python', 'Haskell', 'Javascript'] - now only 6 elements - Rust has gone
```

- the return of the element being removed is particularly useful if you want to do something with it
  - e.g., use it in a message:

```js
let bestLanguage = languages.pop(); //store the popped element in the new variable
let message = `My favorite language is ${bestLanguage}.`; //note the use of a template literal here :)
message;
//'My favorite language is JavaScript.' (JavaScript is the last element in the list now)
languages;
//(5) ['Fortran', 'C', 'Erlang', 'Python', 'Haskell'] - now only 5 elements - JavaScript has gone
```

- .shift() method:
  - removes the first element:

```js
let worstLanguage = languages.shift();
message = `My least favorite language is ${worstLanguage}.`
message;
//'My least favorite language is Fortran.'
languages;
//(4) ['C', 'Erlang', 'Python', 'Haskell'] - now only 4 elements - Fortran has gone from the beginning
```

- 'queue':
  - data structure where new items are added to the end and removed from the beginning
    - think about how a queue of people works
  - implemented using these four methods (push, unshift, pop, shift)

#### Combining Arrays

- .concat() method:
  - adds two arrays together:
  - creates a new array (leaves original arrays untouched)
    - not a mutating method


```js
let fish = ['Salmon', 'Cod', 'Trout']; //initialize variable fish as array
let mammals = ['Sheep', 'Cat', 'Tiger']; //initialize variable mammals as array
let animals = fish.concat(mammals); //use the .concat() method on the fish variable to add the mammals to the end
animals; //call the animals variable
//(6) ['Salmon', 'Cod', 'Trout', 'Sheep', 'Cat', 'Tiger']
```

- to concatenate three or more arrays, pass multiple arrays as the arguments to .concat():

```js
let originals = ["Hope", "Empire", "Jedi"];
let prequels = ["Phantom", "Clones", "Sith"];
let sequels = ["Awakens", "Last", "Rise"];
let starWars = prequels.concat(originals, sequels);
starWars;
//(9) ["Phantom", "Clones", "Sith", "Hope", "Empire", "Jedi","Awakens", "Last", "Rise"]
```

#### Finding the Index of an Element in an Array

- .indexOf(element) method
    - returns index of _first_ time element is found only
    - if not found, returns -1:

```js
let sizes = ["Small", "Medium", "Large"];
sizes.indexOf("Medium");
//1 - Medium is the second element so index [1]
sizes.indexOf("Huge");
//-1 - Huge is not in the array so -1 is returned
```

```js
let flagOfArgentina = ["Blue", "White", "Blue"];
flagOfArgentina.indexOf("Blue");
//0 - only the position of the first Blue at position 0 is returned
```

#### Turning an Array into a String

- .join() method:
    - converts array to a single string, joining all of the elements together:

```js
let beatles = ["John", "Paul", "George", "Ringo"];
beatles.join();
//'John,Paul,George,Ringo' - comma between elements by default
```

- can pass any valid string as a separator other than the default comma as the argument:

```js
beatles.join(""); //empty string as separator
//'JohnPaulGeorgeRingo' - no separator now
```

```js
console.log(beatles.join"&\n"); //pass an ampersand and new line escape character as the separator
/*
John&
Paul&
George&
Ringo - separator only appears between elements, not after each one. Ringo is last so no ampersand after him 
*/
```

- any non-string values will be coerced to strings:

```js
[100, true, false, "hi"].join(" - "); - //this time calling the method on the array literal itself, rather than on a variable as above
//'100 - true - false - hi' - one long string
```

#### Other Useful Array Methods

- arr.includes(element) - returns true if given element is in the array
- arr.reverse() - reverses the order of the elements - mutating method
- arr.sort() - sorts the elements as if they were strings - mutating method
- arr.slice(start, end) - creates new array extracting elements from original array by index from inclusive start to exclusive end. 
  - If no arguments supplied, entire array is copied into a new array
  - useful if you want to apply a mutating method to the array but keep the original array as is
- arr.splice(index, count) - removes count elements from array, starting at index

## Objects

### Creating Objects

### Accessing Object Values

### Setting Object Values

### Working with Objects

#### Getting an Object's Key

#### Getting an Objects Keys and Values

#### Combining Objects

## Nesting Objects & Arrays

### Nesting with Literals

### Nesting with Variables

### Exploring Nested Objects in the Console

### Printing Nested Objects with JSON.stringify
