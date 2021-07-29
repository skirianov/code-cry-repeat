---
title: '#0 - Execution Context, Hoisting and me'
date: 2021-07-28 15:40:35
tags: javascript
---

## Scene set-up

Imagine. No. **IMAGINE**

It's a pleasant evening, just after dawn. You, wearing fancy cloths, standing in front of the best theatre in town. You've got a free ticket to a play with rather a weird name "JavaScript Engine". You thought - *Why not?* and now you are here. 

Enter the hall. Get a drink at the bar. You hear a ring, the play is about to start. Once you found your seat, the lights slowly dimmed and stong highlight pointed towards the scene. Announcer slowly centered himself in place and welcomed you all on a journey to JavaScript engine.

## How JavaScript engine works - Execution Context

Just like you are reading a play, that's how JavaScript engine "reads" your code. Top to bottom. Line by line. 
When you read a play, all the characters, actions, interactions and comments are stored in your head, from where you understand what is happening. Now this is actually Execution Context.

**IMAGINE**

Now, you are on the other side of the scene. You are the director of the play. A well known and popular director and your plays are always as per the book. You are very pedantic, you know. No one can say, that book was better ;)

You have a scenario in front of you. Like in any play, first you have the list of the characters. Then their interactions. And then comments and environment descriptions somewhere in between. This, you are setting up the world of the play, where everything is stored and where every character lives. That is the plot. 

Same, the JavaScript engine, when parsing your code, creates a Global Execution Context. The Global Execution Context is split in two phases: **Creation** and **Execution**. 

During the **Creation** stage, you as a director will create a world, you will create characters and write down how they will interact. The JavaScript engine will do the same. It will create a *"world"* - **window** object and reference to it **this** variable, then it will create *"characters"* - allocate a memory for variables and set them as 'undefined', and then it will store their *"interaction"* - placing function declarations entirely in the memory. 

When everything is set-up, to perform a play you actually need actors. So, now you are entering the **Execution** stage. You are looking for actors and then tell them how to play, and what to play. And again, JavaScript engine doing exactly the same. During **Execution** stage, it will assign *"actors to the characters"* - assign values to the variables, then it will make them *"play their role"* - invoke the functions.

So, to make it clear, at Global Execution Context at Creation Phase - JavaScript first creates a world the code will run in with **this** refered to it, creates a memory for values and keeps them 'undefined' and stores functions into memory. Then, during Execution Phase - JavaScript assigns values to variables and execute the functions. If you ever struggle with 'hoisting', that's basically it. You just nailed it. 

**Hoisting** is just the name. Your code is only read by JavaScript engine from top to bottom. But, because it was initially assigned a value of 'undefined', the later declared variables, will be still 'undefined' when you try to access them. You can't just interact with the actor, who is not even in a play, right?

Wait, but I said, that first it creates a Global Execution Context. Is there anything else? Well, yes. There is a Function Execution Context.
See, once you understand the idea of Global Execution Context, the Function one is simple. It's like a play in a play. You know, like Inception.

Only, when Function Execution Context goes through a **Creation** phase, it actually does not care about a global variable, what it actually cares about are arguments.

So in case of a Function Execution Context - JavaScript first creates a local world of arguments with **this** refered to them, being provided from the global world, then it creates a memory for local variables and sets them 'undefined' and then stores inner functions to the memory. And things go on and on, as deep as you nest functions within functions.

## Summary

Hope this abstraction actually clarified things for you. In a matter of simplifying information, I have split the topic in few separate posts. If you feel that this concept is clear for you, please proceed to next one [#0.1 - Call Stack, Closures and me]().
The whole idea of this blog is to make you imagine the processes, so please read and then close your eyes and let you imagination do the rest for you.

Please, feel free to contact me, if something was not clear, or you have sugestions to make. I am open for conversation.

See you around.