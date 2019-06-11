# Functional Programming with Ramda

## About me 

Hi there fellow humans! I'm Edie an expat from São Paulo, Brazil living in Wroclaw for the past 2 years. I hold a degree in Computer Science and have worked with front end technologies for about 5 years now.

Along with my team at NVM, I work in designing and implementing exciting reusable components written in React based on our proprietary component's library.

When I'm not coding, I like playing guitar and reading books. Other two passions I have are traveling and bike riding.

*Note: Is drinking hot cocoa everyday considered a hobby?*

## What you will learn 

What is Functional Programming (FP for short), its principles and the many benefits of working with it. 

We will be using Ramda to assist us in ilustrating some of FP's fundamental concepts and making our code more elegant and readable (with its pointfree style approach).

Ramda is a javascript library which provides lots of general-purpose functions to help you write functional code faster and elegantly.

## Audience

Suitable to devs who have worked with Javascript or any other programming language.

## What is functional programming?

> Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — [Wikipedia](https://en.wikipedia.org/wiki/Functional_programming)


## Origins

The foundation of FP lies in the abstract mathematical theory of computation involving Lambda calculus **originally developed in the 30s** by the mathematician Alonzo Church.

![Alonzo Church](http://scihi.org//wp-content/uploads/2012/08/alonzo3.jpg)

## Core principles

**Function purity**
: The same arguments always produce the same results
: It causes no *side effects*

**Immutability**
: Data never changes (they are copied and transformed instead)

**Declarative over imperative approach**
: Focus on what to execute instead of how
: Allows easy composition via Higher Order Functions

### Pure functions vs Inpure functions
In order for us to fully grasp this concept, let's use an example to ilustrate the concept. Suppose we want to calculate an employee's yearly pay raise. 

We could achieve this by using the formula below:

`New Salary = (Old Salary X Raise %) + Old Salary`


### Inpure function example

```

let YEARLY_SALARY = 50000
let RAISE =  0.04

const payRaise = salary => (salary * RAISE) + salary

payRaise(YEARLY_SALARY) // 52000

```

### Pure function example

```

let YEARLY_SALARY = 50000
let RAISE =  0.04

const payRaise = (salary, raise) => 
                        (salary * raise) + salary

payRaise(YEARLY_SALARY, RAISE) // 52000

```

### Immutability

### Immutability example

### Declarative over imperative approach
Before we dive deep into the differences between both approaches, let's briefly refer to their definitions.

#### Imperative vs Functional approach

| Characteristic | 	Imperative approach | Functional approach |
| ----------- | ----------- | ----------- |
| Programmer focus | How to perform tasks (algorithms) and how to track changes in state. | What information is desired and what transformations are required. |
| State changes | Important. | Non-existent. |
| Order of execution | Important. | Low importance.
| Primary flow control |	Loops, conditionals, and function (method) calls. |	Function calls, including recursion. |
| Primary manipulation unit	| Instances of structures or classes. |	Functions as first-class objects and data collections. |
*Source MSDN*

The idea behind the algorithm below is to allow an item in the list to be marked as selected or unselected. 

#### Imperative approach example
```
const toggleSelectedItem = (id, items) => items.map(
  item => {
    if(item.id===id){
      if(item['selected']){
        const {
          selected,
          ...noSelected
        } = item
        return noSelected
      }else{
        return { ...item, selected: true}
      }
    }else{
      return item
    }
  }   
)
```

#### Declarative approach example

```

const select = assoc('selected', true)
const unSelect = dissoc('selected')

const toggleSelectedItem = (id, items) => map(
  when(
    propEq('id', id),
    ifElse(
      has('selected'),
      unSelect,
      select
    )),
  items
)

```

## Where's the data?

You might have noticed from the previous example that in no way we referred to an instance of items. This is possible due to the application of partial functions and currying. 

This technique is called **Point free style**. 

## Conclusion

At this point we have a better understanding of Functional Programming, a bit of its history and an overview of its principles.

We also learned that by using FP our code becomes much more elegant and predictable.

At the end we were introduced to Ramda and how its *point free style* helps us produce much more elegant code..

***

![questions](http://www.quickmeme.com/img/d3/d39566077d8af3ebee098c2ad682cba790d1ce3006a119a6fc6b7079b59c49f0.jpg)



