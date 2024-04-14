---
id: fcnnsa51rlui6g7h090jx54
title: 06 Classes
desc: ''
updated: 1712946126795
created: 1712860540802
---
A tool for generating multiple objects with shared characteristics and behaviour

## Creating Classes and Instances

- templates for standardised objects
  - automate the process of creating objects
    - syntax similar to calling a function
  - two main elements:
    - the properties each object of the class should have (property =  key:value pair)
    - the functions the object can access
      - functions are called methods when part of a class

- e.g., in a game, player class might include:
  - properties for name, health, position ...
  - methods to move around, fire a weapon, pick things up ...
- class can be used to create multiple players (i.e., several objects)
  - each object within the class is an _instance_ of the class
    - with its own details for the values of the properties

```js
class Player { //'class' keyword to declare a new class; class name ('Player') - customary to start with upper-case letter
    constructor(startX, startY) { //body - just like a function body; define two methods. here, the constructor method - just like a function but no 'function' keyword
        this.x = startX; //two parameters - startX and startY - assigned to instance's x and y properties - keep track of position
        this.y = startY; //'this' keyword refers to the current instance being created - dot notation as for other object properties
    }

    move(dx, dy) { //this second method updates player's position
        this.x += dx; //changes y property based on dx/dy parameters
        this.y += dy; //'d' stands for 'delta' - referring to how much something changes 
    }
}
```

- Constructor method automatically called each time an instance is created
  - performs the necessary setup for the object:
    - receiving any parameters defining the instance
    - laying out the properties

- Create an instance of our new player class:

```js
let player1 = new Player(0,0); //use the 'new' keyword followed by class name and parameters in parentheses
//parameters then passed to constructor method
```

1. new empty object created
2. hidden link to class created
3. constructor method is called automatically
    - new object accessible with keyword 'this' - sets properties
4. arguments passed to constructor's parameters
5. new object returned

- can now interact with the new object:

```js
player1.x;
//0
player1.y;
//0
player1.move(3, 4);
player1.x;
//3 - i.e., 0 + 3
player1.y;
//4 - 0 + 4
player1,move(2, 2)
player1.x;
//5 - i.e., 3 + 2
player1.y;
//6 - 4 + 2
```

- when method called on object, 'this' keyword is set to current object
  - above, 'this' is bound to player1
- the method can therefore be shared with multiple objects
  - 'this' becomes whichever object receives the method call
- use dot notation to call the method
  - just as with built-in methods for strings and arrays

- **Functions vs Methods**
  - method always associated with an object
    - defined on an object
    - called on an object - dot notation:
      - _str_.slice()
      - _arr_.push()
    - object on left of dot is _receiver_
      - methods can access and modify receiver using 'this' keyword
  - function stands alone
    - no dot notation as no receiver

## Inheritance

- method for defining relationship between classes
  - child classes inherit properties and methods from parent classes
    - useful to share general set of behaviours
    - saves from having to repeat this general code
  - child classes aka _subclasses_
  - parent classes aka _superclasses_

```js
class Actor { //this class is not intended to be instantiated - it is a parent for the child classes below
    constructor(startX, startY) {
        this.x = startX;
        this.y = startY;
    }

    move(dx, dy) {
        this.x += dx;
        this.y += dy;
    }

    distanceTo(otherActor) { //takes another Actor as a parameter and returns distance to that object
        let dx = otherActor.x - this.x; //calculate horizontal distance
        let dy = otherActor.y - this.y; //calculate vertical distance
        return Math.hypot(dx, dy); //use built-in Math.hypot() method to calculate hypotenuse of the distances - standard technique for calculating distance on a 2D plane
    }
}
```

- Actor is an _abstract class_ - a generic entity in this game
- the following Player and Enemy classes based on Actor are _concrete classes_ that will be created and represent something solid

- redefine Player class to inherit from Actor
  - include specific property hp (hit points) to show health - how much the player has been attacked:

```js
class Player extends Actor { //use 'extends' keyword to make a subclass of Actor - no move & distanceTo methods needed as inherited from Actor
    constructor(startX, startY) {
        super(startX, startY); //'super' keyword refers to constructor from superclass (Actor) - when created Player constructor called automatically, which then calls Actor constructor (via 'super')
        //pass startX and startY to Actor constructor to set Player's xy properties
        this.hp = 100; //set player in full health when created
    }
}
```

- create new Enemy class also inheriting from Actor, extending with an attack method to attack Players
  - has no extra properties in constructor so no constructor created
    - where a subclass has no constructor method, the parent class constructor method called automatically upon creation of instance

```js
class Enemy extends Actor { //declare enemy class to extend Actor (as with Player) but no extra properties needed in constructor
    attack(player) { //only unique method
        if (this.distanceTo(player) < 4) { //takes Player object as parameter and checks distance - distanceTo method inherited from Actor. Can attack if distance is less than 4
            player.hp -= 10; //reduces Player health by 10 hit points
            return true; //to indicate a successful attack
        } else { //if distance 4 or greater, attack fails
            return false; //returns false to indicate an unsuccessful attack
        }
    }
}
```

```js
let player = new Player(1, 2);
let enemy =  new Enemy(3, 4);
player.hp;
//100
enemy.distanceTo(player);
//2.8284271247461903 - close enough to attack
enemy.attack(player); //attack
//true - successful
player.hp;
//90 - player has lost 10 hp
player.move(5, 5); //player moves
enemy.attack(player); attack
//false; attack unsuccessful - distance > 4 (4.242640687119286)
player.hp;
//90 - player's points remain at 90
```

### Try it Yourself

- create new class called Follower:
  - extends Actor
  - takes three constructor parameters:
    - startX, startY, player
      - startX & startY passed to Actor's constructor
      - player parameter saved as property on the object as with Player's hp property
  - follower can't be attacked so no hp needed
  - follows assigned player
    - needs a follow method updating x,y to match player's

```js
class Follower extends Actor {
    constructor(startX, startY) {
        super(startX, startY);
        this.player = player
    }
    follow(player) {
        this.x = player.x;
        this.y = player.y;
    }
}
```

## Prototype-Based Inheritance

- older mechanism alongside newer class system, commonly found in older code:
  - a constructor function to create and return new objects
    - a regular, standalone function - not defined within a class
    - called using 'new' keyword
  - a _prototype_
    - an example object used by constructor as a model
      - new objects inherit from prototype
- class inheritance actually built on top of this older system - _syntactic sugar_
  - class inheritance is just an alternative syntax for prototype inheritance

### Using Constructors and Prototypes

- JavaScript creates links between the constructor, the prototype, and the new instance:

```js
function Cat(name) { //constructor function
    this.name = name; //name parameter using 'this' to set the object's name
}
//when the constructor function is created, it automatically gets a prototype property
//prototype accessible with dot notation as for any other property - an object to act as a model
Cat.prototype.sayHello = function () { //adding a method to the prototype (sayHello) and setting its value to a function expression
    console.log(`Miaow! My name is ${this.name}.`) //logs a greeting including the name of this particular cat
}

let kiki = new Cat("Kiki"); //create new cat called Kiki and pass her name to the constructor
kiki.sayHello(); //call the constructor method on kiki - hidden link to Cat.prototype to find the sayHello definition. 'this' keyword set to kiki in this instance
//Miaow! My name is Kiki.
```

- syntax for creating an instance is exactly the same as when using a class

```js
kiki;
/*> Cat {name: 'Kiki} - created with the Cat constructor
   name: "Kiki" - name property with value "Kiki" - assigned when constructor called
   >[[Prototype]]: Object - kiki has a [[Prototype]] property - the hidden link from which kiki is inherited (Cat constructor prototype)
     >sayHello: f() - a value that is a function (f) - the sayHello method from the prototype
     >constructor: f Cat(name) - the Cat constructor function - the other part of the hidden link
     >[[Prototype]]: Object
```

### Comparing Constructors and Classes

- chain between instance to prototype to constructor
  - enables JavaScript to locate the methods and properties for the instance
- classes do the same:

```js
class Dog { //equivalent to the Cat constructor function above
    constructor(name) {
        this.name = name;
    }

    sayHello() {
        console.log(`Woof! My name is ${this.name}`);
    }
}

let felix = new Dog("Felix");
felix;
/*>Dog {name: 'Felix'}
   name: "Felix"
   >[[Prototype]]: Object
     >constructor: class Dog - points to a class rather than to the constructor function in kik above
     >sayHello: f sayHello() - found via prototype link just as for kiki above; however, has a function name here, which it doesn't for kiki (anonymous function) 
     >[[Prototype]]: Object 
*/
```

- can access object's prototype property directly through the name \__proto__

### Exploring Object.prototype

- if no explicit constructor function used to create an object, it uses the built-in Object constructor function
  - Object.prototype contains basic methods that all objects should inherit
    - the end of the line in chai of prototype references
- Kiki was created with Cat constructor
  - but Cat.prototype was not explicitly created with a constructor
    - used Object constructor instead
      - prototype is therefore Object.prototype
        - hence the inner \[[prototype]]

- An object created with an object literal also has no explicit constructor function
  - therefore created with Object constructor
    - Object.prototype as prototype

### Walking the Prototype Chain

- when asking for object's property or method, JavaScript first checks the object itself
  - if not there, it looks to object's prototype
    - if not there either, it goes on up the chain until it gets to Object.prototype - **walking the prototype chain**

```js
kiki.name; //access name property - set directly on kiki itself
//'Kiki'
kiki.sayHello(); //call sayHello method - found on kiki's prototype - first checks on kiki and then checks the prototype
//Miaow! My name is Kiki.
//undefined
kiki.hasOwnProperty("name"); //this is a method from Object.prototype - so kiki's prototype's prototype
//true
kiki.madeUpMethodName(); //non-existent method. JS walks the entire chain - kiki->Cat.prototype->Object.prototype
//>Uncaught TypeError: kiki.madeUpMethodName is not a function
//   at <anonymous>:1:6 - cannot find the function anywhere and throws an error
```

### Overriding a Method

- By understanding the prototype chain and locating the object's methods, we are able to override the definition of a method that would be inherited from the prototype
  - enables us to inherit most of a prototype's behaviour while making some unique
- When method is called, JavaScript uses the first definition it finds as it walks the chain
  - if a method defined directly on the object has same name as method defined on the prototype, the method on the object takes precedence

```js
let moona = new Cat("Moona");
moona.sayHello = function () {
    console.log(`HELLO! I'M ${this.name.toUpperCase()}!`);
};
moona.sayHello();
//HELLO! I'M MOONA!
kiki.sayHello();
//Miaow! My name is Kiki.
```
