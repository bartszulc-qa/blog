---
layout: post
title: Behaviour Driven Development - Part 1
description: "My first encounter with BDD, or at least how I understood BDD back then."
modified: 2014-09-28
tags: [bdd, agile, scrum, testing, article]
image:
  feature: logo.jpg
comments: true
share: true
---

Assuming you read my prologue to the series about BDD, you should be fairly familiar with the basics. Interested in how I started with BDD? You never guess...

## Automation

I started with Automation. I know it doesn't make much sense now, but it did to me back then. I mean, you still hear "Cucumber" as an answer to question "Do you do BDD in your project?", which is similar to asking developer whether he does TDD, and getting "Yes, I implement unit tests in JUnit"... which doesn't make much sense, right?

### BDD as yet another testing tool

There was a time when I understood BDD as yet another tool that help me automate my tests rather than a delivery process.

I'm an engineer, master of engineering in the matter of fact. Graduated Technical University, Computer Science, and since I remember have been enjoying programming. Me being an Agile Tester meant me being a Developer, different kind of Developer of course, a Developer who is focused on testing rather than features. Whose responsible is in implementation automated tests, test frameworks and tools, test harnesses. 

I had my framework for Acceptance Tests I was very proud of. The framework could work exercise web applications tailored for desktop and mobiles. Built on top of Robotium and WebDriver. Utilizing all the best practices and patterns, like Page Objects, Page Factories, Loadable Components. Where test configuration had been managed by Maven, Jenkins, and WebDriver Grid. Pretty awesome. Even did few presentations and workshops so people could learn themselves how to build such thing.

In the framework I had am abstraction layer of instrumentation, Page Objects. I had another layer responsible for configuration, Jenkins and Maven. I clearly needed another. More layers I say! Cucumber helped me with that. With Cucumber I didn't need to write execution code, I could use natural language. Cucumber, not only is a test runner, but also helps you link your scenarios in Gherkin with automation code.

{% highlight gherkin %}
Scenario Outline: As a user I want to find nearby stops to post code of my choice
	When I search for <postcode> from the home page
	Then the following list of nearby stops is returned
	| stopname			| stopcode			| towards			| routes			|
	| <first-stopname>	| <first-stopcode>	| <first-towards>	| <first-routes>	|
	| <second-stopname>	| <second-stopcode>	| <second-towards>	| <second-routes>	|
	| <third-stopname>	| <third-stopcode>	| <third-towards>	| <third-routes>	|
	| <fourth-stopname>	| <fourth-stopcode>	| <fourth-towards>	| <fourth-routes>	|
	
	Examples: Stops nearby a postcode
	| postcode 	| first-stopname 		| first-stopcode 	| first-towards 						| first-routes 										| second-stopname 		| second-stopcode 	| second-towards 							| second-routes 									| third-stopname 		| third-stopcode 	| third-towards 					| third-routes 	| fourth-stopname 				| fourth-stopcode 	| fourth-towards 			| fourth-routes 			|
	| N17 		| Scotland Green (B) 	| 57704 			| towards Manor House or Stamford Hill. | 149,  259,  279,  341,  349,  476,  N76,  N279 	| Lordship Lane (R) 	| 73479 			| towards Northumberland Park or Edmonton. 	| 149,  259,  279,  341,  349,  476,  N76,  N279 	| Pembury Road (X) 		| 47842 			| towards North Middlesex Hospital. | 318 			| Pembury Road (T) 				| 75293 			| towards Stamford Hill. 	| 318 						|
	| WC1 		| Russell Square (J) 	| 59177 			| towards Aldwych. 						| 59,  68,  91,  168,  N91 							| Southampton Row (B) 	| 76501 			| towards Waterloo or Trafalgar Square. 	| 59,  68,  91,  168,  188,  X68,  N91 				| Russell Square (C) 	| 55923 			|  									|				| Russell Square Station (H) 	| 91209 			| towards Euston. 			| 59,  68,  91,  168,  N91 	|
{% endhighlight %}

{% highlight java %}
@Then("^the following list of nearby stops is returned$")
	public void compareStops(List<Stop> expectedStops) {
		List<Stop> matchedStops = getProvider().getResultsPage().getStops(
				expectedStops.size());
		getDriver().captureScreenshot();
		assertEquals(matchedStops, expectedStops);
	}
{% endhighlight %}
My test framework was finally complete. I had all the layers I wanted! Let's have another run with presentations, workshops, training. Let's talk about how I have BDD in my project now...

### Result

Hope I don't need tell you extending my testing framework by Cucumber had no affect on delivery. Even worst... it had negative impact of the quality of product, as it degraded. What happened then?

I had to spend more time on implementing new features in the test framework... and maintain these features. Yet another abstraction layer made the whole solution more complicated. Harder to maintain. I found myself in a vicious circle. To extend the framework I needed to invest more time in order to learn about best development practices and tools. When I implemented tests with it, they started failing, giving false negatives, were very brittle, unpredicted. To maintain tests I had to spend even more time I already didn't have, and all these effort covered only activities of the  second quadrant of Agile Testing Quadrants...

Delivery didn't improve. Why not? Nothing changed in terms of the process. I just took the assumptions we had about the product and its feature and created feature files based on them. Nothing more. No illumination moment in between.

First attempt, first failure, but I learnt a lot.

#### Agile Tester

Being tester in Agile isn't only about automation. In fact some people may struggle with automation and leaving the task to them may not only impact project, but also the person. I had to understand I can ask other people for help. Maybe when I don't feel capable in particular tool or language, I should ask a developer for help, and learn from him. This didn't cross my mind back then. I needed to prove myself. Prove I'm a developer. Instead of pairing with experienced developer, I struggled, and my solution had been continuously increasing technical debt (yes, testers also have to consider Technical Debt while implementing their automated tests and other fixtures requiring code). It took me a while to understand tester in Agile must leverage all the available opportunities that help him find time to work through quarters of the Agile Testing Quadrants, and more, not get stuck on particular activity. And learn... from others in your team.

#### Test Pyramid
As the automated tests began to be painful to maintain, I started analysing my tests in terms of scope, level of details, utilized  interfaces - access layers, I came up with several questions.. Does every test need to exercise application from the most top layer, User Interface? Does every test need to be so unstable because of unrelated conditions, like network latency? Does every test need to take so long to execute and return result? Hope not. This is when I first came across Test Pyramid - the perfect structure of automated tests. 

![Test Pyramid (c) Martin Fowler]({{ site.url }}/assets/img/test-pyramid.png)

At the bottom of the pyramid, at the foundations, you will find Unit Tests (so called small tests, low in scope, high in details), which focus on classes, methods, are very autonomous thus they gave most credible results. They are also very fast, as you don't need to set up special context for them to run in, they just need the class they test, that's it. As these tests build foundations of the pyramid, you should have a lot of them, more than any other type of tests.

In the middle you will find tests that exercise many units building services (so called medium tests, medium in scope and details). These tests are slower comparing to Unit Tests, as their need to spawn a context with all the classes, their configuration, integration details. There are also less credible, more error prone, than small tests, as they require all the units to work correctly, and may require communication over network. You may test the components through an API. As these tests are in the middle of the structure, you should have fair number of them, not too much, not to little, just enough.

At the top of the pyramid are end to end tests, big tests (high in scope, low in details), that require all the components, all the applications in a system, to work together. These are the tests you would normally execute from user perspective, through User Interface. These tests are the most unreliable. Not only dependent components may not work correctly due to various reasons, including environmental and configuration, but you may also encounter issues specific to distributed systems, like networking and concurrency. These tests are also very slow. Not only you need to provide proper environment with all the components available for them to start, but you also are affected by latencies in communication between these components, limited resources, and so on. You should have limited number of such tests. Only the most crucial behaviours from the business and technical risk should find themselves at the top of the pyramid.

In some implementations of the pyramid there is an additional layer, covering manual or exploratory tests. I prefer the second implementation.

So how my tests looked comparing to the ideal structure. Not so good. In fact it looked like I turned the pyramid upside down. Instead of the expected structure I ended up with something that looked line an ice cream cone, with Acceptance Tests as BDD Scenarios as ice cubes. Something clearly wasn't right.

![Test Pyramid (c) Martin Fowler]({{ site.url }}/assets/img/test-cone.png)

#### Doubts

I started having doubts. BDD doesn't work. I have my scenarios in Gherkin. I have Cucumber. But still what we deliver is not what is expected, and my tests are a mess. Few questions kept recurring,

- Does every test scenario is an acceptance scenario I need to format in Gherkin?
- What should be the level of details of my acceptance scenarios? Should I be very detailed as other testers are with scripted tests? Should I include all the steps I take in order to set a system in proper state in scenarios, and do the same for assertions?
- As a tester, should I care only about Acceptance Scenarios, the Examples, or is there more to my work?
- Is BDD a testing framework?
- Is there an equality sign between BDD and test automation? What is the origin of test automation and why we care about it so much now?

### Benefits

Although the main objective hadn't been met - delivery didn't improve - there were some benefits to the whole idea of including Cucumber into the test framework... other than me learning stuff of course :) 

We had had a leaving documentation. An executable documentation. The way our system behaved was represented as Scenarios, written in natural language, which continuously looked after potential regression issues. We were able to fairly fast spot a breaking change, inform product owner about potential issues and impact on feature. We even didn't need to do that as he were able to read the results himself. He didn't need to analyse what a particular method name of JUnit really means. He could just read a scenario, check its status, and relate to it.

It also became easier for inexperienced testers, business representatives, managers, to use the framework to implement automated tests. You didn't need to know Java or Python. You just needed to copy and paste available steps and order them properly, or extend example table by new cases.

I may be a little harsh. I'm pursuing the main goal of BDD. It may happen that what your team needs is a DSL (Domain Specific Language) tool that will help people implement automated tests and provide a leaving documentation. For instance, you may not be responsible for support and maintenance of developed application, and in order to ease the handover and reduce frustration on both sides, future maintainers and you, you may want to write down what your system does, how it behaves, in BDD scenarios. Not only you will have a documentation the support could read in order to learn about your system, but they would also have a safety net for their changes.
Or maybe you work on a legacy system, and as you learn the system you would like to store your findings in some place. Why not use Gherkin for that? As you team will refactor the legacy code, they will know, with some degree of certainty, how their change impacted the system. In the matter of fact, probably when you work on legacy system the whole concept of Test Pyramid doesn't make much sense, and you would want to start from the top of the pyramid, implementing end to end tests that give you some comfort level, and gradually move down the pyramid, start implementing smaller tests.

Everything depends on the context, on what you want to achieve, what resources you have in dispose, and what are the constraints or regulations you have to comply with.

## Pivot

My first attempt to BDD, in some degree, was beneficial, and I definitely learnt a lot about test automation. Still, the main objective wasn't met. I needed to pivot.

Wait for the next post to learn more about my struggles with BDD.