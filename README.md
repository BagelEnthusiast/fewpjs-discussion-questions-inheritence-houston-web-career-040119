# OO JS Discussion

## Objectives

* Practice reading and reasoning about code
* Discuss events with out

## Exercise

Take a look at each of the code samples below. For each sample, work with your group to answer the following questions.

1. What does each line of code do?
2. How does this piece of code work?
3. Given this code sample, what can you learn or describe about JavaScript

**NOTE**: The below code is for demonstration purposes only. Typically, when a property begins and ends with `__`, that's a signal to you as a developer not to mess with it. This is sometimes referred to as "syntactic vinegar" - making something difficult to do so we don't do it.  

### Example 1

```javascript
class Dog {
  bark(){
    return "Woof!"
  }
}

const fido = new Dog()
fido // Dog {}
fido.bark() // 'Woof!'
fido.__proto__ // {constructor: ƒ, bark: f}
fido.__proto__.bark() // // 'Woof!'
```

### Example 2

```javascript
class Animal {
  walk(){
    return 'Walking...'
  }
}

class Dog extends Animal {
  bark(){
    return "Woof!"
  }
}

const fido = new Dog()
fido.__proto__ // Animal {constructor: ƒ, bark: ƒ}
fido.__proto__.__proto__ // {constructor: ƒ, walk: ƒ}
fido.bark() // "Woof!"
fido.walk() // "Walking!"
fido.__proto__.__proto__.walk() // "Walking!"
```

### Example 3

```javascript
class Animal {
  walk(){
    return 'Walking...'
  }
}

class Dog extends Animal {
  bark(){
    return "Woof!"
  }

  walk(){
    return "Walking on four legs"
  }
}

const fido = new Dog()
fido.walk() // "Walking on four legs"
fido.__proto__.walk() // "Walking on four legs"
fido.__proto__.__proto__.walk() // "Walking..."
```

### Example 4

```javascript
// NOTE: Just a reminder, do not try this at home.
class Dog {
  constructor(name){
    this.name = name
  }

  walk(){
    return "Walking on four legs"
  }
}

const fido = new Dog("Fido")
fido // Dog {}
fido.__proto__ = Array.prototype

fido // Dog {}
fido.length // 0
fido.push(1)
fido // Dog [1, name: "Fido"]
fido.length // 1
fido.push(2)
fido.map(num => num * 2) // [2, 4]

fido.name // "Fido"
fido.walk() // VM697:1 Uncaught TypeError: fido.walk is not a function
fido.walk // undefined 

```
