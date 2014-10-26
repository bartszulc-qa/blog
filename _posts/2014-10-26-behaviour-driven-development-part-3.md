---
layout: post
title: Behaviour Driven Development - Part 3
description: "BDD and Three Musketeers."
created: 2014-10-26
tags: [bdd, agile, scrum, testing, article, story]
image:
  feature: logo.jpg
comments: true
share: true
---

Behaviour Driven Development is build from two parts, Behaviour and Driven Development. Maybe as with User Stories if the order got reversed it would be easier for people, including myself, to understand what is really all about.

It's not really about Test Automation and writing Test Scenarios in Gherkin. Although it might help your Automated Tests become easier to understand and compel you to think about your Automation more as you write your Scenarios in Given, When, Then manner.

It's not about Living Documentation, describing all the behaviours and features of the System you work on, and running constant checks. It helps, but you can do that without BDD.

It's also not only about defining Behaviours, thinking about User Stories and their relation to Business Features, refining Acceptance Criteria by creating Scenarios and Examples. Thus as you understand the complexity behind laconinc words you may decide to cut down on scope earlier.

It's about putting everything together and Driving Development with Behaviours.

![Behaviour Driven Development]({{ site.url }}/assets/img/behaviour-driven-development.png)

## Three Musketeers

As I discussed in earlier posts, you can't expect people who are not participating in meetings where conversation on new behaviours is taking place, to drive their work with what's been decided on these meetings. First, there is a matter of unanswered questions, unknowns and risks that have not been discussed during the meetings. Second, there are social aspects of exclusion.

While discussing new behaviours do proper Three Musketeers meetings. Include business, developers, and testers representitives. Together you will work together on requirements, help understand and refine the work that needs to be done, work on User Stories and their Acceptance Criteria, ask questions regarding business domain and processes, understand business language, and by creating Scenarios and defining Examples understand the scope, find answer for your known unknowns, realize hidden unknown unknowns, and all these to understand the complexity behind a task before you start sizing it. On the other hand, your Business representatives get closer to Development, understand Development needs and risks, avoid asking Developers to deliver too much in a Sprint, redefine their expectations and shape Product Backlog.

You really can't do these meetings without Business. You have an issue understanding what is needed, not the Business. They know what is needed, they may not know if you know, but this is a completely different question. You are the one who should ask as much questions as possible, as much as is needed to get to the bottom of a change. On the other hand, business should be available to give you answers, help you understand complex processes and domain, allow you to poke in their heads in order to understand what is hidden behind few terse sentences.

It's in all best interest to deliver the right thing, and the conversation that takes place during Three Muskeeters meetings is a way of learning what is the right thing.

### and the role of Tester

Should you, as a Tester, participate in these meetings? Couldn't Business just talk to Developers, and the other way around? Why Three not Two? First of all, you're seen as the Quality Guy, responsible for delivering the right software, the software your client expects. You need to understand what is expected from you before you test implementation and confirm what's been delivered is right. There is no need for you to exclude yourself from the meetings and learn from second hand what's been discussed. This is an unnecessary risk. You have questions as well.

Your feedback, as a person, who might have the best understanding of the system and all its components, integration, user expectations, and so on, is very crucial. You might be the one who will first spot problems with integrating components while implementing new Behaviours of Business Features, or notice how the new changes may impact already available Features. At the end it's your role to know how everything works together.

Your soft skills are also useful. You might be the one whose role is to bridge the gap between Development and Business. Help Business understand complex Technical Jargon, and help Developers work on Business Vocabulary. Encourage both, Developers and Business, to actively participate in the meetings. Check if everything is understood, if anyone has anything to add. Become a moderator. Don't let one of the parties to hijack the meeting. Learn about Behaviour Driven Development and help participants as they come up with Scenarios. Volunteer to be the Scenario writer.

![Three Musketeers]({{ site.url }}/assets/img/three-musketeers.jpg)

## Hidden benefits

All the benefits of Behaviour Driven Development, the discussion you take to understand expectations, have been presented throughout the whole cycle. You gain understanding, that helps you size stories. You focus on the essence, as you know what is expected from you to deliver and what's not. You control the state of your system, as you have all the behaviours of your Product in a single repository, a living documentation.

You may get even more. Your developers may want to continue working on Behaviours as they implement them. Not by changing them, but by implementing the glue code that binds Scenarios written in Gherkin and are stored in feature files, with the implementation of your Test Scripts. They may find better ways of checking if a behaviour is implemented the right way. Instead of testing everything from the end user perspective through a Web Interface, use interfaces hidden from the user, like the API of Web Services, or specific classes. This way your runs may become faster and less brittle. You will also gain support so the costs of maintaining the glue code and feature files decrease. The cost already should be lower, as you can be sure best practices were used to implement the code, and thus technical debt is reduced.

The team becomes responsible for the Third Quarter of Tester in Agile. Now we are responsible for creating and maintaining Story Tests, not only me. This means more time for me to do other types of testing, other activities. Should I start looking into low level testing? Should I run the production code against Sonar and see how the metrics look like and what they say? Should I spend more time understanding the end user, how he will interact with our system, what kind of devices, operating systems and web browsers he may use? Or should I check my competition, see if they have problems with security or performance and suggest including these tests in our product Test Approach? Now you have time for these action points, it's up to you and the team to decide what might be the most beneficial for you to work on.

## Answers to remaining questions

As you remember I raised several issues as I approached BDD for the first time. Some of these questions have already been answered in my previous posts, but there are still some that need answers, like...

- Are Acceptance Tests the only Tests I should care about?

Yes, and no. It all depends. Do you have time and people to care about other tests? If no, focus on Acceptance Tests, make sure your team has confidence in what is implemented in terms of Business Value. Regarding other tests, raise an impediment, a risk, to your Scrum Master or Product Owner. Your developers should already have covered First Quarter activities that support the team and are technology oriented.

- Is BDD a testing framework you should use for all your tests?

No, it's not. BDD is not about tools. There are tools that support BDD, but the conversation about features is more important. You shouldn't use tools just because there popular or because they give you more features. The question is, do you really need those features? Are those features essential for your testing or are you forcing yourself to find application for them? As a tester you should use tools that offer only features that are essential. Make sure your tool makes what is expected from it, nothing more, nothing less. Make sure it's fast and has good community that can support you. More features, more complications, higher price. No matter whether the tool is open source or not. At the end you will need to spend time to learn it and maintain tests implemented with it, and time is money.

- Where does the idea of automation come from? BDD?

Definitely not. This is the mistake you may do if you start considering BDD by the tools that are out there to support the process. The emphasis on automation, including test automation, comes from working in Agile environment, where you can't spend weeks running your regression tests as it's expected from you to have working software without regression issues and new features within a week, two weeks, cycles. You need to automate your tests to make them faster and more reliable. Tools like Cucumber help you automate your Scenarios and create a Living Documentation of your System, so you don't need to run them manually after every change you make.
