---
layout: post
title: Unity for Progammers #1 - WTH?
description: Unity can be confusing at first because where's the code and the glue?
categories: unity-for-programmers
---

When I first started looking at Unity3D I wanted to shut it down and return to 
[Libgdx](https://libgdx.badlogicgames.com/), [Love2D](https://love2d.org), or [Pyglet](http://pyglet.org).
Basically, anything where I could get back in control of my program and make things work.

I mean what is this nonsense of drag and drop to make things? That's great for just
sketching something out, but I'm a coder. I want to WRITE CODE!

### Changing my view

My first step to coming to terms with this was by recognizing how I was approaching Unity 
and my projects in general:

 * Did I want to make a game that people played, or did I want to write code that was just a framework?
 * How much did I really enjoy troubleshooting collision detection logic or coding up tweener logic?
 * Was I really as good in the root level as I thought?

Everything really started to clear up for me when I was integrating various Entity-Component Systems (and/or
building my own) with Box2D or other Physics engines that are out there (Chipmunk, etc...)

*Is this really all that fun to wire up all these libraries or would I accomplish more if I just started 10 steps further a long the path?*

It's probably obvious to anyone outside. But let's be honest, writing code is fun. And starting with a blank slate is
a pretty incredible experience. So much so we can lose sight of our real goals.

So, I took the leap to stop wiring everything together and start looking at my game from the outside in. That's
where everyone else is playing it and as a builder and designer that's how we need to approach it.

### Composition, and patterns

The more I worked with Unity the more I appreciated what was happening. My first few attempts were creating
very clunky scripts with lots of complex logic and weird behavior. But as I got more comfortable with the toolset
the patterns began to emerge:

**Composition** over inheritance - Each Game Object in Unity is really just a container. This is common in
 any standard ECS (Entity-Component System) framework. But what was interesting in using a designer to help build
 your game is how easy it is to just create another object to represent something instead of trying to bundle everything
 together. Also, just like the standard [Composite Pattern](https://en.wikipedia.org/wiki/Composite_pattern) hierarchies
 of objects can simplify your code drastically. 

 For example, one problem I ran into early was trying to rotate an image (cute little bunny) that had a Rigidbody attached.
 Whenever I rotated the object, the collision detection went crazy! I was a little frustrated at first and went the *coder's*
 route of figuring out how to disable collisions, and reactivate them... It was becoming a mess and I knew there should be
 an easier way. There is, just make a child of the main game object that is just an image and rotate the child. The parent
 keeps it's rigidbody and behaviors but the image is now simply rotating. Problem solved! Elegantly
 and actually with a cleaner design. This gets at the heart of using this tool. If something is really hard, you are 
 probably thinking about the problem wrong.

**Other Patterns** - Also, the more I worked with the scripting layer the easier it was to see all the other patterns that
could be applied. Since everything is just a .NET assembly, using Singletons, Publish-Subscriber, etc... was easy to see. 
And not only that, but the GameObjects themselves could represent bases of these patterns. For example, a GameObject that
is a spawner of enemies is really just a Factory. 

**Scripts as Behaviors** - Something I'm learning now that I will share in a more detailed post is focusing Scripts around
behaviors as opposed to trying to code the game specifically in each of them. An example is having a health system that
eventually kills the Gameobject off. First instinct could be to have the player and the enemies have two different systems
since really when the player dies, something different will happen than when an enemy dies. But the reality is that from
a health SYSTEM perspective, they both just died. Make another script that deals with the differences of the death behavior
don't mingle that in your health system.

### Where to start

The following are resource I've been using. There are probably even better ones out there and maybe it will be possible
to build up a list of these resources at some point:

 * [Udemy Unity Programmer Course](https://www.udemy.com/unitycourse/) - Best part about this is the community around it. 
 The programming will be very trivial for an experienced coder, but that is almost a win here. On each lesson you will be
 moving far beyond the topics but learning how a beginner would approach it helps teach the fundamentals and expose the flaws in it.
 Also, having projects layed out is a good way to stay focused on learning something. Usually this course is on sale, so don't pay full
 price for it.
 * [Reddit Unity2D](http://reddit.com/r/Unity2D/) A good forum that frequently has tutorials posted in it
 * [Unity Tutorials](http://unity3d.com/learn/tutorials) Unities tutorials are good and simple too. Definitely a good jump start location


Thanks for checking in. I will have more detailed examples and lessons now that I have this off my chest. 

Keep Coding!
