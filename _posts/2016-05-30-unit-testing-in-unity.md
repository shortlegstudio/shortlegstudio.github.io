---
layout: post
title: TDD in Unity
description: Making TDD fast in Unity
categories: unity-for-programmers, tdd, unity3d
---

My experiences learning Unity3D have been all over the map. I've built a large
variety of learning and sample projects that taught me fundamentals of working
within Unity but every time I'd start to end up in a similar point.

I'd reach a points where:
  1. My logic would have some weird flaky bug that was hard to reproduce.
  1. I would have lots of FindObjectOfType<T> and GetComponent<T> calls sprinkled throughout my code.
  1. I would like to add a new behavior or mechanic and find I would need to touch many parts of the system in order to incorporate.

Now, this is no different from my experience in the world of building business applications.
There we are always running into this problem that our business logic gets
mingled up in our frameworks and persistence. We become so tied to the way things
are done that we can't build the interactions that are interesting to do.

This got me interested in TDD inside Unity. But we run into the following big problems:
  1. TDD in Unity3D is SLOW. Using the standard methodology you need to flip between Monodevelop and Unity to run the tests. This is even worse than TDD in Rails, and that's saying something.
  1. You cannot unit test Monobehavior classes.

I mean, that right there will kill off pretty much anyone from really attempting
TDD inside Unity. Interestingly, the solution is the same as it is for Rails or
any other system that is heavily dependent on a framework. Remove the dependency
on the framework.

I was watching this [Uncle Bob video](https://www.youtube.com/watch?v=WpkDN78P884)
and I was intrigued. Could we apply similar principles to a Unity3D project?
So far my experience has been "Yes, of course!". But it does require a different
methodology to thinking about your project.

Now, I'm still filling in the organizational details that will make this work
out but I have a few guiding principles that have allowed me to generate far
more unit tests, be able to rapidly test them (less than a second to run the suite),
and not only that. I've found that my ability to add new functionality has
accelerated. Granted, this project right now is focused on an NPC Generator.
I'm totally willing to have everyone doubt this in the realm of a FPS, or other
more action based environment.

In a coming post I'll start to highlight how I have begun to isolate my logic
behind Gateways and Boundaries so that my core mechanics know nothing about Unity
and I can actually create unit tests that cover these behaviors.

-T
