---
title: '#0 - Execution Context, Hoisting and me'
date: 2021-07-28 15:40:35
tags: javascript
---

This is the first post of the series "JavaScript and me". JavaScript fundamentals may be overwhelming and difficult to understand. This blog posts are reflection of my understanding of concepts and aimed to help others, who may struggle to grasp them.

Today we will look at the fundamentals of how JavaScript running behind the scenes. Today we will be JavaScript ourselves.

## Execution Context

What is this? **Execution Context** is the process JavaScript Engine is using to interpret your code. It is simply a splitting of one big and complicated task into small easy steps. Understanding of this topic is *essential* to see the big picture. Other advanced topics will get much clearer once you get it.

## Global Execution Context

JavaScript "reads" your code from top to bottom. Line by line, like you read this post. The first thing happens when you run your ***.js*** file is the creation of Global Execution Context. This process consists of two phases: **Creation** and **Execution**.

**Creation Phase**

***Imagination ON***
You are the writer. You want to write a new book. What will you do first? Right, create the world. You will *create* a foundation of the story - the world, where your *characters* will exist and live. Like a global object everyone refers to. *this* world.

Once the world is created, you want to add some *characters*, right? Empty world is no fun, you know. Somebody who will *interact* with each other and the world. Let's do it. Let's declare their existance and function. 

A while after, the story is completed. The book has become a new bestseller. Hollywood wants to film it now.
***Imagination OFF***

When JavaScript Engine parses your code it *creates* a global object `window` and variable `this` which refers to that object. Memory is allocated for variables. Their names stored and assigned a value of 'undefined'. 


```
  var foo = 'bar';
  var person = 'John Doe';

  function sayHi() {
    console.log('Hello world!')
  }
```

![creation-phase-code-snippet](https://blog.skirianov.com/images/creation-phase.png)

> JavaScript running in the browser will create `window` object and running in Nodejs will create `global` object.

**Execution Phase**

***Imagination ON***
Now, you are a famous Holywood Director, you've got the script for that new book everyone is talking about and big bosses wants it to be filmed. The world has been created for you already, it just needs to be brought to life. You have noticed, that script is not written very well and sometimes new characters appear in the middle of the chapter. But you are a visioner, you are well known for following the scripts like a machine, no one can say that book was better.

You start hiring actors and *assigning* them to the characters. Then. Camera! Motor! Action! You are filming them acting, *functioning*. 

And that's it. Movie is ready. Oscar is your, no doubt.
***Imagination OFF***

At the Execution Phase the JavaScript Engine is assigning values to the variables stored in memory and ininitializing functions.

![execution-phase-code-snippet](https://blog.skirianov.com/images/execution-phase.png)

**Creation and Execution Phase**

The Execution Phase starts when Creation Phase is over. If you look closely, you will spot that because all the variables have been stored with value of 'undefined' during Creation Phase, you can actually call them before they were assigned a value. This leads us to the next concept - Hoisting.

## Function Execution Context

Function Execution Context follows almost identically same principles as Global Execution Context. Only difference is, that Function Execution Context is not creating another `window` object, as it can be created only once, but instead it creates an `arguments` object. This "arguments" object is local and accessible only within the context of that function.

It is like the *world* created inside the global *wowld*.

## Hoisting

During the Execution Phase variables declared with `var` will be accessible, even before values were assigned to them, because they already store 'undefined' and it will not cause a Reference error. Variables declared with `let` and `const` will be only initialized during Execution Phase and values assigned at that moment, hence trying to access this variables before will lead to Refence error. 

On the other hand, Functions have been fully stored in memory during Creation Phase, which allows us to invoke them even before they have been initialized at the Execution Phase. 

Ability to invoke functions before initializing is called **Hoisting**. 

## Summary

I hope this was helpfull and made things clear. This is very fundamental topic, which I recently was not aware of and most of beginner guides are missing this. Even while I was writing draft of this post, I have got better understanding how recursion works. Please feel free to contact me if you find something wrong or if there anything you would like to add. 

See you around!