---
layout: post
title: Behaviour Driven Development - Prologue
description: "What is BDD? How BDD fits into testing? What is my experience with BDD?"
modified: 2014-09-27
tags: [bdd, agile, scrum, testing, article]
image:
  feature: logo.jpg
comments: true
share: true
---

Behaviour Driven Development has been on hype a while now, and still gaining on popularity amongst agile software development teams. More and more companies adopt BDD to help their teams understand business requirements better, and by that achieve the sole purpose of development, delivering software that meets client, or more general, shareholders expectation. 

In many cases User Stories and Acceptance Criteria are simple not enough for the development team to clearly understand what is expected from them to deliver. BDD helps refine expectations by defining examples of feature behaviour as scenarios. It becomes a formalized method of communication between various interest groups targeted at product features. 

## Succeeding through failure

I've been working with Behaviour Driven Development for some time now. I'm definitely not an expert, doubt I'm even experienced BDD adopter. Nevertheless, I have some experience in BDD. In fact I probably went through all the possible stages of failing with BDD, and this is the base for the article. I won't write about how to succeed with BDD... but how to fail. 

I find it easier to succeed when I know all the symptoms of failure. I also find it easier for people to relate to a failure rather than success... or maybe it's just Polish thing.

## What is BDD?

Before I start the journey, I need to elaborate on Behaviour Driven Development first.

### ... and how is it related to TDD

Whenever I talk about BDD, I always refer to TDD - Test Driven Development. You may ask what one method has in common with the other? Clearly TDD is more technical centric than BDD. You may say T stands for Technical, and B for Business, and you are probably right. At the end TDD is about writing tests for units of code, while BDD is about defining behaviours of a product feature. However, when you look closely, you find TDD isn't really about testing as it's about design. Developer, before coding, has to look at the implementation, or rather an vision of the implementation, from a different perspective, perspective of an user, another unit. 

Writing tests first is just a way of placing yourself as a consumer of your unit. You look at the unit as a provider of particular functionality, the unit behaves in certain way, and you're trying to capture all the behaviours, implement tests for them first, then code, and refactor. One behaviour at a time. 

Wait a minute, a behaviour? Doesn't' the B in BDD stands for behaviour too? Yes, and that's why I think BDD has a lot in common with TDD. The concept of analysing an unit, whether it's a feature or a class, by behaviours, before the development starts.

### The process

The process itself is pretty straight forward. You start with a feature, come up with all its behaviours, capture them as scenarios, properly formatted, and use them to drive development.

Assuming you're member of a SCRUM team, you may want to discuss features and define scenarios during Backlog Refinement and/or Sprint Planning meeting. Just seat with your colleagues, representing different interest groups, development, testing, and business (so called Three Amigos), and discuss what exactly needs to be implemented as part of the iteration. The idea is to focus on intention not implementation. In summary, grab an User Story, check related feature, implemented or extended by the Story, agree on Acceptance Criteria, and come up with examples for the Criteria as BDD Scenarios while refining the Criteria. 

Three Amigos is the main difference between BDD and TDD. While in TDD you can easily implement good unit. talking only with yourself, you really can't do that with features. You simply don't have enough knowledge, not so technical as domain. 

You may argue in TDD you have peer review, either by pair programming or code review, but still, you are having a conversation with members of the same group, development. You need more than that to implement proper feature not only developers will use.

### The outcome

The outcome of the meeting? A feature file (or files). Literally a file with extension feature.

{% highlight gherkin %}
Feature: Search
	Allows users to search by street name
	Allows users to search by post code
	Recognizes partial street names
	Recognizes partial post codes
	Responds with error message on empty search
	Responds with info message on no result

	Scenario: Search by full street name
		Given 'Example Street' is a known street
		When user searches for 'Example Street'
		Then he gets 'Example Street' as a result

	Scenario: Search by partial street name
		Given 'Example Street' is a known street
		And 'Barely Example Street' is a known street
		When user searches for 'Example Street'
		Then he gets 'Example Street' as a result
		And he gets 'Barely Example Street' as a result

	... and so on
{% endhighlight %}

Feature is defined by a title (next to the Feature keyword), and a description (free form text under the the Feature keyword). Description might be, for instance, a list of all the Acceptance Criteria taken from various User Stories related to the feature.

Scenario also has a title, and a list of steps that actor has to take in order to observe particular behaviour. There are three categories of steps. Step can be preluded with Given, When or Then. Given stands for a precondition, prerequisite, something that must happen before actor can interact properly with a feature, that sets the system in particular state, and thus allows scenario to start. When is an event trigger. The interaction with a feature. Then is expected outcome of the action. Steps can also begin with And or Or so you can specify many prerequisites, actions or outcomes, and how they relate to each other. This format is known as Gherkin.

The neat feature of Gherkin is that it integrates with tools that support automation, such as Cucumber, and has implementation in many natural languages, so you don't have to teach your shareholders English, which might be a problem if you are, for instance, developing software for Polish government (not saying that it's the bad idea for Poles in government to learn the language... though... giving it second thought, maybe they shouldn't have implemented Gherkin in Polish).

### The goal

Feature files, or rather their contents, should drive the development through the iteration and... reduce the risk of delivering software that doesn't meet expectations. Where implemented features doesn't work according to the defined scenarios. 

As a developer you use the suite of feature files as a continuous reminder, a verification of what you do is right, and whether the state of system is right.

### ...but I heard BDD is about testing and stuff

..and I'm probably making the same mistake, including a post about BDD in a testing blog, because it isn't really about testing. 

Sure, it helps with testing. You can transform created BDD Scenarios to Test Scenarios, and include automated tests with Cucumber into your regression suite. But you can do that without BDD. You just leverage created artefacts for the purpose of testing.

BDD Scenarios fit into second quarter of Agile Testing Quadrants, so the quarter that supports team, by increasing the chance of delivering the right software, and is business facing, as scenarios are written in high level and business language.

![Agile Testing Quadrants by Lisa Crispin]({{ site.url }}/assets/img/agile-testing-quadrants.png)

But BDD isn't a testing technique as it. It's a way of delivering software by understanding behaviours of required features. It's more about communication and conversation between different groups, finding common language, than it's about testing. At least to me.

Nevertheless, I'm a tester and have something to say about BDD, and as one of my kind, you really should  leverage the opportunity BDD gives you. Participate in Three Amigos meetings. Ask questions you normally ask during Sprint. Help refine features. Come up with more Acceptance Criteria, more Scenarios, more User Stories for later implementation. Use created Scenarios as Acceptance Scenarios. Automate. Validate.

## The journey begins

...so where did I start with BDD? You will need to wait for next post to find out... but please keep in mind I didn't know back then what I know now :)