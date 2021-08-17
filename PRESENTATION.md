<!-- background: #232323 -->
<!-- color: #4280ff -->
<!-- font: MFred,sans-serif -->

![](https://www.newvoicemedia.com/images/icons/NVM-Logo-Horizontal-Blue-Vonage.svg)

# Functional Programming with Ramda

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

# About me 

Hi there! I'm Edie and I came from far-far away.

**Education**

Bachelors degree in Computer Science

**Background**

Over 5+ years of experience as a Front End engineer

**Hobbies**

Bike riding, Playing my Ibanez RGD, reading books and traveling

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

# Audience

Suitable to devs who have worked with Javascript or any other programming language.

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

# What you will learn 

**Part 1**
- What is Functional Programming?
- Origins
- Core Principles

**Part 2**
- What is a function?
- Pure functions, Side effects & Immutability 

**Part 3**
- Enter Ramda
- Declarative programming
- Point free style

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

# Part 1
- What is Functional Programming?
- Origins
- Core Principles

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## What is functional programming?

> Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — [Wikipedia](https://en.wikipedia.org/wiki/Functional_programming)

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Origins

The foundation of FP lies in the abstract mathematical theory of computation involving Lambda calculus **originally developed in the 30s** by the mathematician Alonzo Church.

->![Alonzo Church](http://scihi.org//wp-content/uploads/2012/08/alonzo3.jpg)<-

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Core principles

- Pure functions
- Higher Order Functions
- Side Effects
- Immutability
- Declarative approach

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

# Part 2

- What is a function?
- Pure function
- Pure vs impure functions
- Immutability
- Side effects
- Higher Order Function

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## What is a function?

> A function is something that maps an input to an output. 

```js
const square = n => n * n

square(3) // $ 9
```

**However, not everything that looks like a function is a function.**

```js
const magic = () => console.log('Ta-da!')

magic() // $ Ta-da
```

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

->![](https://www.sccpre.cat/mypng/full/130-1303163_wow-comic-book-png-png-download-logo-wow.png)<-

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Pure function

> Is something that always returns the same output for the same input and produces no visible side effects

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Pure vs Impure function

Suppose we want to calculate an employee's pay raise using the given formula:

`New Salary = (Old Salary X Raise %) + Old Salary`

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Impure function example

```js
let yearlySalary = 50000
let RAISE =  0.04

const payRaise = yearlySalary => (yearlySalary * RAISE) + yearlySalary

payRaise(yearlySalary) // $ 52000
```

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Pure function example

```js
const yearlySalary = 50000
const RAISE =  0.04

const payRaise = (salary, raise) => 
                        (salary * raise) + salary

payRaise(yearlySalary, RAISE) // $ 52000
```

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Immutability
> (...) is an object whose state cannot be modified after it is created - [Wikipedia](https://en.wikipedia.org/wiki/Immutable_object)

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Mutation and side effects

```js
let user = {
  name: 'John Doe',
  age: 30
}

const updateUserAge = (user, newAge) => user.age = newAge

updateUserAge(user, 32) // $ { name: 'John Doe', age: 32 }

console.log(user) // $ { name: 'John Doe', age: 32 }
```

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->
## Immutability & no side effects

```js
let user = {
  name: 'John Doe',
  age: 30
}
const updateUserAge = (user, newAge) => ({ ...user, age: newAge })

updateUserAge(user, 32) // $ { name: 'John Doe', age: 32 }
 
console.log(user) // $ { name: 'John Doe', age: 30 }
```

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Side effects

> (...) an operation, function or expression is said to have a side effect if it modifies some state variable value(s) outside its local environment, that is to say **has an observable effect besides returning a value (the main effect) to the invoker of the operation** - [Wikipedia](https://en.wikipedia.org/wiki/Side_effect_(computer_science)

**Example:**
- changing the file system
- inserting a record into a database
- making an http call
- **mutations**
- printing to the screen / logging
- obtaining user input
- querying the DOM
- working with Math.random

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Higher Order Function

> Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions (...) - [Eloquent Javascript](https://eloquentjavascript.net/05_higher_order.html)

```js
import * as R from 'ramda'

const hasMessage = R.compose(
  R.not,
  R.isEmpty
)

hasMessage('Hello world!') // $ true
hasMessage('') // $ false
```

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

# Part 3

- Enter Ramda
- Declarative vs Imperative example
- Point Free Style

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Enter Ramda

> A practical functional library for JavaScript programmers - [Ramda's official page](https://ramdajs.com/)

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Javascript canonical functions are not always pure

```js
// VanillaJs
const fruits = ['Apple', 'Banana'] 

fruits.push('Orange') 

console.log(fruits) // $ ['Apple', 'Banana', 'Orange']

// With Ramda
import * as R from 'ramda'

const fruits = ['Apple', 'Banana'] 

R.append('Orange', fruits)

console.log(fruits) // $ ['Apple', 'Banana']

```

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Declarative programming

> In computer science, declarative programming is a programming paradigm—a style of building the structure and elements of computer programs—that expresses the logic of a computation without describing its control flow - [Wikipedia](https://en.wikipedia.org/wiki/Declarative_programming)

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Imperative approach example
```js
const toggleSelectedItem = (id, items) => items.map(
  item => {
    if(item.id!==id){
     return item 
    }

    if(item['selected']){
      const {
        selected,
        ...noSelected
      } = item
      return noSelected
    }else{
      return { ...item, selected: true}
    }
  }
)
```

***

<!-- background: #ffd558-->
<!-- color: #232323-->
<!-- font: MFred,sans-serif -->

## Declarative approach example

```js
import * as R from 'ramda'

const select = R.assoc('selected', true)
const unSelect = R.dissoc('selected')

const toggleSelectedItem = (id, items) => R.map(
  R.when(
    R.propEq('id', id),
    R.ifElse(
      R.has('selected'),
      unSelect,
      select
    )),
  items
)
```

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Point free style

> [Point-free] is a programming paradigm in which function definitions do not identify the arguments (or "points") on which they operate - [Wikipedia](https://en.wikipedia.org/wiki/Tacit_programming)

***

<!-- background: #ffd558 -->
<!-- color: #232323 -->

## Why we love Ramda?

- Tons of small, ready to use functions
- No side effects 
- Parameters are not mutated
- Easy composition via Higher Order Functions & Point Free style
- Supports Tree-Shaking (unused code is removed from bundle)

***

->![questions](http://www.quickmeme.com/img/d3/d39566077d8af3ebee098c2ad682cba790d1ce3006a119a6fc6b7079b59c49f0.jpg)<-
