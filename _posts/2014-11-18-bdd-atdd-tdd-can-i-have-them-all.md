---
layout: post
title: BDD, ATDD, TDD - Can I have them all?
description: "BDD, Recap."
created: 2014-11-18
tags: [bdd, atdd, tdd, agile, scrum, testing]
image:
  feature: logo.jpg
comments: true
share: true
---

Assuming you've read my posts, you're pretty familiar with BDD - Behavior Driven Development. You probably also know what ATDD - Acceptance Test Driven Development is, and what TDD - Test Driven Development, are.

You may ask, wouldn't it be nice to have all three concepts driving your development together? Is it even possible?

I think it is.

You start by defining Behaviors of your product Features. Discuss User Stories, their Acceptance Criteria. Undertand what is that you know, and what is that you don't know.

Don't think about implementation at this stage. Focus on the outcome, as you were using your system without help of any interface. As you were one.

Write down expected Behaviors as Scenarios. Use the Given, When, Then, to give them a structure. Be declarative. Focus on intent. Build your ubiquitous language you use to document various aspects of your domain. Build the living documentation. Single source of truth.

Remember about the negative space. Flush out all the known unknowns first. Discover unknown unknowns. Appreciate the time you, business experts, and developers, invest to work out differences and misunderstandings.

Make these scenarios executable so you can validate the development. Implement glue code as you progress with the production code.

This is the BDD phase.

Know what is expected? What behaviors should the system you build perform? Start thinking about implementation.

How are you going to achieve a particular behavior? What are the high level tests that can help you realize what is required? Tests taken by an actor, an end user, or another system you interact with?

Write down these Acceptance Tests. Extend available Scenarios. Be more imperative. Put implementation details. Use the BDD tools.

What will the actor exactly need to do with your application in order to achieve a behavior? What will be the ways of interacting with your system? How will he interact with it? Would he need to fill a form? Use this information to drive your development. Use the feedback the results of these tests give you to improve your code.

This is the ATDD phase.

Have a concept of a design in your head that will address a part of an Acceptance Test and get you closer to accomplishing the great goal, having a feature behaving particular way? Drive the concept with tests.

How should the unit work? What functions should it fulfill? Is it a self-sustained entity or require help from other units? Are tests for these units done? Implement unit tests, or maybe integration tests fit better here? Go through the whole cycle, red, green, refactor.

This is the TDD phase.

Repeat until Unit implemented.

Repeat until Acceptance Test passed.

Repeat until Behavior achieved.
