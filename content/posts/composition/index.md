---
title: 'Composition, Composition, Composition'
date: 2026-02-06T00:00:00-05:00
draft: false
author: Keith Henderson
tags: ['programming', 'godot', 'gamedev']
---

# Composition Over Inheritance

I got the itch again to start playing around with Godot, as I often do. This time I wanted to use Godot to practice a concept I
had learned about called Composition. If you are not familiar with the concept, you should because it has literally changed 
how my brain works.

When you write in a language like C# it is "Object Oriented Programming". When you learn this there is a strong emphasis on
inheritance. Inheritance is the "Is-A" relationship. For example; a _dog_ is-a _animal_. A _sports car_ is-a _car_. Typically this means that
you can extend the parent class to the child class using the : after the clsss name then the name of the parent. Inheritance is not a bad thing but when you are working with
something like making a video game it can create tight coupling and inflexibility. This is not always ideal. 

In contrast composition is the "Has-A" relationship. For example, a _car_ has-a _engine_. A _computer_ has-a _cpu_. In this setup
your classes will hold references to other objects as instance variables. The benefits of this is that you get loose coupling and flexibility
with your components. The downside is that you might use a bit more boilerplate code to create and manage more objects.

# When To Use It?

The real question becomes when do you use one over the other? I find myself using composition way more often in Godot. I think this makes
sense when you are making something like a game because you can build complex objects from simpler ones. Overall I would say that I am
really trying hard to favour composition over inheritance whenever I can. I'm finding it easier to maintain and manage my code. If something
is wrong with my player movement for example I know _exactly_ where to look to fix the problem.

# Changing My Brain

Since diving in and forcing myself to constantly challenge my initial ideas and ensure I'm designing with a composition first mindset
I've noticed that how I think about things in general has changed. I do a lot of work with data and pipelines in my day job. I've found
myself rethinking ways that existing architecture can be improved by adopting this mindset. Not just the design, but also how things
are being processed as well. I'm going to keep working at it and might add some devlog type updates here as well.

Cheers,

Keith
