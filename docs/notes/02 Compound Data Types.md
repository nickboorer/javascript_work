---
id: cilhezepe7hpjdmd0cafetj
title: 02 Compound Data Types
desc: ''
updated: 1712597617270
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

- key value pairs (like Python dictionaries)
- values accessed by keys rather than indices
- generally store multiple pieces of info about an entity
  - often not the same data types:
    - name - string
    - age - number
    - married? - boolean
  - Each piece of info gets meaningful name (key) so much clearer what the info means than in an array

### Creating Objects

- object literal {"key": value, "key", value ...}
  - colon between key and value
  - keys are always strings

```js
let casablanca = {
    "title": "Casablanca",
    "released": 1942,
    "director": "Michael Curtiz"
}; //written on separate lines for readability - not necessary
casablanca;
//{title: 'Casablanca', released: 1942, director: 'Michael Curtiz'}
```

- quotation marks not needed for keys if they are _valid identifiers_
  - any set of characters that can be used to create a JS variable name:
    - letters
    - numbers
    - "_" and "&"
  - Other characters can be used in keys, but only when enclosed in quotes

```js
let obj = { key1: 1, key_2: 2, "key 3": 3, "key#4": 4}
obj;
//{key1: 1, key_2: 2, key 3: 3, key#4: 4}
//key 3 contains an empty space, so is not a valid identifier, and key#4 contains a #
```

### Accessing Object Values

- call name of object with key in square brackets:

```js
obj["key 3"];
//3
casablanca["title"];
//'Casablanca'
```

- If key is a valid identifier, then you can use dot notation rather than square brackets:

```js
obj.key_2; //won't work for key 3 or key#4
//2
```

- similar to syntax for .length above
  - property just another name for a key-value pair
    - JavaScript treats strings and arrays as objects behind the scenes

### Setting Object Values

- same notation as to look up a value:

```js
let dictionary = {};
dictionary.mouse = "A small rodent"; //dot notation (mouse is a valid identifier)
dictionary["computer mouse"] = "A pointing device for computers"; //square bracket notation (computer mouse contains a space so is not a valid identifier)
dictionary;
//{mouse: 'A small rodent', computer mouse: 'A pointing device for computers'} 
```

### Working with Objects

- object methods called as _static methods_ (methods defined directly on the constructor instead of on the object): Object.method(object)
  - pass the object as an argument
  - the first Object. is a _constructor_ (a type of function used to create objects)
    - it is NOT the name of the object

#### Getting an Object's Keys

- Object.keys() - returns an array of all of the keys of the object:

```js
let cats = { "Kiki": "black and white", "Mei": "tabby", "Moona": "gray" };
Object.keys(cats);
//(3) ['Kiki', 'Mei', 'Moona']
```

#### Getting an Object's Keys _and_ Values

- Object.entries(object) - returns an array of two-element arrays, first element of each inner array is the key, the second element is the value
  - very useful for loops

```js
let chromosomes = {
    koala: 16,
    snail: 24,
    giraffe: 30,
    cat: 38
};
Object.entries(chromosomes);
//(4) [Array(2), Array(2), Array(2), Array(2)]
//drill down:
/*
0: (2) ['koala', 16]
1: (2) ['snail', 24]
2: (2) ['giraffe', 30]
3: (2) ['cat', 38] 
length: 4
[[Prototype]]: Array(0)
*/
```

#### Combining Objects

- Object.assign(object) - combines multiple objects into one:

```js
let physical = { pages: 208, binding: "Hardcover"};
let contents = { genre: "Fiction", subgenre: "Mystery"};
//we have two separate objects, both about the same book
```

- combine the two objects into a single object "book":

```js
let book = {};
Object.assign(book, physical, contents); 
book;
//{pages: 208, binding: "Hardcover", genre: "Fiction", subgenre: "Mystery"}
```

- first argument is the "target" - the object to which the keys from the other objects will be assigned
  - an empty object in this case but that doesn't have to be
  - if you use an existing object as the target, it will be modified
    - this is probably something you want to avoid so you usually want to use a new, empty object as the target

```js
Object.assign(physical, contents); //here the existing object physical is the target so it will be modified
physical;
//{pages: 208, binding: "Hardcover", genre: "Fiction", subgenre: "Mystery"}
```

## Nesting Objects & Arrays

- objects can be nested within outer objects, just like arrays
- arrays can be nested within objects and objects within arrays as well
  - more sophisticated data structures
- created by either:
  - creating object or array literals with nested objects or arrays inside; or
  - creating inner elements, saving them to variables and then using the variables to built the composite structures

### Nesting with Literals

```js
let trilogies = [ //an array...
    { //...of two elements, each with the same keys
        title: "His Dark Materials",
        author: "Philip Pullman",
        books: ["Northern Lights", "The Subtle Knife", "The Amber Spyglass"] 
        //this books key contains an array: an array within an object within an array!
    },
    {
        title: "Broken Earth",
        author: "N. K Jemisin",
        books: ["The Fifth Season", "The Obelisk Gate", "The Stone Sky"]
    }
];
```

- accessing an element in one of the inner arrays requires both array indexing and object dot notation:

```js
trilogies[1].books[0]; //the first book (0) from the second trilogy (1)
//'The Fifth Season'
```

### Nesting with Variables

- create objects containing inner elements
- assign objects to variables
- build outer structure from variables:

```js
let penny = {name: "Penny", value: 1, weight: 2.5};
let nickel = {name: "Nickel", value: 5, weight: 5};
let dime = {name: "Dime", value: 10, weight: 2.268};
let quarter = {name: "Quarter", value: 25, weight: 5.67};
//create four variables, one for each type of coin
```

```js
let change = [quarter, quarter, dime, penny, penny, penny];
//create an array of the specific coins in the jar
//note the repetition - an advantage of creating the variables first
```

- access by combination of array indexing and object dot notation:

```js
change[0].value; //returns the value of the first coin in change (a quarter)
//25
```

- the repeated elements share a common identity
  - all of the pennies share the same values
  - if any of those values change, they can be updated once in the object in the Penny variable and it would carry through to all instances of the element in the change array:

```js
penny.weight = 2.49; //change weight of a penny and check it has carried through to all of the pennies in Change
change[3].weight;
//2.49
change[4].weight;
//2.49
change[5].weight;
//2.49
```

### Printing Nested Objects with JSON.stringify

- View nested objects by turning them into JSON strings
  - JSON = JavScript Open Notation:
    - textual data format based on JavaScript object and array literals
    - used to exchange and store information on the web
  - JSON.stringify(object) - converts object to JSON string:

```js
let nested = { //a deeply nested object!
    name: "Outer",
    content: {
        name: "Middle",
        content: {
            name: "Inner",
            content: "Whoa..."
        }
    }
};
```

- convert nested to a JSON string:

```js
JSON.stringify(nested);
//'{"name":"Outer","content":{"name":"Middle","content":{"name":"Inner","content":"Whoa..."}}}' - this is the JSON string
```

- contained within single quotes
- equivalent of the original object literal used to create nested
  - braces to enclose object
  - colons to separate keys from values
  - commas to separate key:value pairs
- only missing line breaks and indentations
  - can insert by adding arguments to the JSON.stringify(object) method:
    - JSON.stringify(object, replacer function _(modify output by replacing key:value pairs)_, spaces & newlines)

```js
nestedJSON = JSON.stringify(nested, null, 2); //object = nested, replacer function = none, number of spaces to indent = 2
console.log(nested.JSON);
/*{
  "name":"Outer",
  "content": {
    "name":"Middle",
    "content": {
      "name":"Inner",
      "content":"Whoa..."
      }
    }
} this is the JSON string with the line breaks and indentation added*/
```
