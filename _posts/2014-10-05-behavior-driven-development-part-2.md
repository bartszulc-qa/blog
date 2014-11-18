---
layout: post
title: Behavior Driven Development - Part 2
description: "BDD as a way of gathering requirements."
created: 2014-10-05
modified: 2014-10-11
tags: [bdd, agile, scrum, testing, article, story]
image:
  feature: logo.jpg
comments: true
share: true
---

Clearly BDD isn't about tools and automation, it's about... improving requirements. In order to understand better what is expected from me, I have to talk to the origin of requirements, the business representatives.

## Talking to Business

I have started having regular meetings with business representatives, including Product Owner, Business Domain Experts and Business Analysts. First meetings focused on helping understand the non-technical guys what BDD is all about, or rather how to properly create feature with their scenarios in Gherkin. Helping them understand all the different keywords, like Given, When, Then, even Feature, and how they relate to well known User Stories and Acceptance Criteria. Gradually, as our knowledge had grown, we have started creating more and more scenarios, focused on intention, not implementation, and the unknown rather than what is clear.

### User Stories, Acceptance Criteria... and BDD

BDD extends standard SCRUM approach with User Stories and Acceptance Criteria in many ways. Starting from the top of a feature file, you don't describe Scenarios for User Stories, instead you create them for Business Features. You can't easily link Business Features to User Stories. You may need to implement new Business Feature as part of User Story, but at the same time, you may only modify a behavior of already implemented Feature, or drop it completely. User Story has became a way of managing delivery within a SCRUM. A way of slicing big chunks of work, Business Features, into smaller, manageable pieces, a team can deliver within a Sprint. Why is it so important to focus on Business Features and not User Stories while working with BDD? User Stories are transient, their life cycle is bound to a Sprint, while Business Features are certain, they live with the product. You want your Scenarios to reflect the system behavior at any given time, and to do so you need to include not only all the behaviors implemented as part of the current Sprint, but all of them implemented so far. You need all the Features, and their Behaviors.

Now, knowing what a Feature is and how it is related to User Story, let's think about Scenarios and Acceptance Criteria. Normally you'd take a card, and write on one side a proper summary of a User Story, containing all the key elements, answering who needs a change, what is the change, and why it's needed, or in reverse order, where the focus is on the business outcome not the stakeholder, so why particular change is needed asked first, followed by what's the change, and finished with who needs it. On the back of the card you list all the Acceptance Criteria, all the characteristics the change should have in order to be accepted. Card is small and you won't be able to write a lot on it. Your Acceptance Criteria are limited in length. Not detailed enough. Without necessary examples of what you have in mind while writing particular statement, you may find your team confused during planning and delivery. In order to avoid potential issues and reduce the risk, you could put more details regarding Acceptance Criteria on another card. Create Examples of new Behaviors. As you go with writing Scenarios you may find Acceptance Criteria too complex. They may require slicing in order for an User Story to be delivered. You may find Acceptance Criteria missing, as available don't cover particular case. Finally, you may decide User Story is too big for a Sprint and needs to be refined, sliced into smaller Stories, based on what you already discussed while creating Scenarios. The whole process of writing Scenarios, understanding how they're related to Acceptance Criteria, critiquing Scenarios and Criteria, might come with great benefit to your Spring planning and execution. Spending a little more time on thinking what is expected, answering questions raised by different groups, may help avoid critical issues fairly early in the process.

![User Stotry to Acceptanc Criteria to Scenario to Feature]({{ site.url }}/assets/img/user-story-feature.png)

### Agile Tester as a Communication Bridge between Geeks and Suites

As our mutual understanding of BDD had grown, I have started understanding the concept of a Tester in Agile as a communication bridge between worlds of technology and business. On the one hand, I'm the technical representative who can clear out all the technical difficulties behind implementing a change, inform about feasibility and potential cost. On the other hand, I'm becoming more familiar with business domain, language, and processes, and by that can help business refine User Stories, write down Acceptance Criteria, come up with Examples as BDD Scenarios, also improve my testing. All this so developers understand better what is expected from them. All this to improve delivery.

### Result

Unfortunately my meetings hadn't improved delivery as much as I'd wished for. Although developers were provided with feature files beforehand, we still had problems with delivering everything according to requirements. What went wrong? We had BDD Scenarios derived from Acceptance Scenarios. We improved the process of gathering requirements. Why BDD still didn't work? Well...

#### You understand... but others don't

I had to answer a lot of questions regarding business domain and its vocabulary I used to use while writing Scenarios down. What was clear to me, wasn't so clear to developers who didn't participate in meetings. While I had a chance to ask questions whenever something wasn't clear to me, whenever I didn't understand what particular word meant, and what are the available context of use, they had to rely on what was written down. I became a living dictionary answering what is the meaning of a particular word in one context and another. You need to understand BDD doesn't give you any tool that could help you with creating domain specific vocabulary. You can use comments to write down what a particular abbreviation means, but this is a workaround rather than a solution. BDD assumes everyone is familiar with everything that had been written down, including domain specific expressions.

#### You learn... but others don't

As I were getting more and more familiar with the domain and its intricacies, Scenarios became less and less detailed. I didn't need as many examples to understand a concept as I needed the first time. I started building a map in my mind, creating connections between different aspects of the domain, started building patterns. Unfortunately, those who didn't participate in the meetings weren't learning. This caused an waterfall effect. New Scenarios caused more and more confusion, the number of raised questions and issues constantly had been increasing.

#### Everything is clear to you... but not to others

I thought as a tester I will come up with all the cases. Raise all the questions. Refine Scenarios to maximum.  Find all the potential risks in implementation. I was wrong. I had no idea developers will come up with many more cases and questions, crucial to development, the available Scenarios didn't tackle. The negative space where BDD resides, where we look for unknown rather than what is known, can really benefit from developers' input.

In order to mitigate the risk of not delivering a change due to missing details, I'd have started acting as a Proxy Product Owner, a Domain Expert, answering all the questions, writing missing Scenarios, based on my understanding of the Domain. Taking great risk, and basing development on my assumptions. Delivery would look very similar to when we hadn't had BDD at all, with one, crucial exception, now I was taking the risk on my own, back then the risk of delivering according to wrong assumptions was shared between all the team members. This could have resulted in a conflict between me - tester, and developers, and blur the real cause of our problems. Glad I didn't choose to go that way.

The whole situation we found ourselves in looked a lot like Waterfall, a Scrumfall. I had my meetings where it was decided what exactly gets implemented and how. Created documentation was considered detailed enough by authors, but people who had to drive their work by it, couldn't, as they experienced too many unknowns, too many unanswered questions.

While implementing BDD at smaller scale you also need to consider social aspects and how they might impact delivery. Excluding developers from meetings, ignoring their contribution and input, could have a negative impact on their morale and productivity, it would be harder for them to identify with created product, and feel responsibility and accountability for the product success.

#### Benefits

Although the main objective wasn't achieved, we did improve on delivery a little. Also, these two Amigos meetings we had, between me and business, improved quality of requirements, as we have started describing in details new Behaviors of Features. Answering questions normally developers answer during development, like what exactly Acceptance Criteria meant, how the feature should behave, what are the examples of its new/modified behavior. Meetings also helped business understand how not enough details may impact implementation and how hard it's to elaborate on an idea that can be easily fit in a single statement. Everyone has started understanding the complexity behind implementation, how new behaviors may overlap or affect already implemented, and how it may impact usability of the system. In many cases meetings resulted in reduced scope of User Stories.

With every discussion we had, the way Scenarios were written improved. Finally, we found the right level of details our Scenarios should be written in. Not too much and too little, just enough. Focusing on intent, not implementation.

I don't think there is a silver bullet, a recipe for writing Scenarios you could use for all projects and teams. What is clear to me, is that you have to find a common language on your own in order to achieve common understanding. This common language might be different for banking systems, where you probably would operate solely on domain level, and for open source libraries, where your users speak your language, and you can dive into technicalities. In order to achieve the level of mutual understanding, I suggest appointing a coach who, on the one hand, would be responsible for teaching all the participants about BDD, helping understand the structure of a feature file and Gherkin formatting, on the other hand, keep people encouraged to have a discussion, a conversation on Scenarios, who would constantly check with people if everything what has been written down is understood, does anyone has questions, is there anything unclear. Who would look for a boredom as a sign of getting too much into details or writing too vague Scenarios.

The other good thing besides finding common language, is that the structure of my automated tests had started looking more like a Pyramid than a Cone. On the top which you'd find created with business help Scenarios in Gherkin, and as you'd go down the structure, more limited in scope and rich in details test scenarios, derived from their parents. Created, either, by starting from the top, taking slice of a high level Scenario, de-constructing it, creating all the cases for all its boundaries, and gradually moving down the structure by rerunning the de-construction process, or by starting from the bottom, implementing unit tests for a class, then moving to integration tests binding many classes, and finally finding yourself at the top, having everything you need to cover a business Scenario. You could also combine these two approaches, start from the top and the bottom, and find yourself in the middle. This is probably the best approach as it requires tester and developer working together, where tester takes the responsibility for the top, high level test scenarios, and developer for the bottom, low level test scenarios. While taking the last approach, discuss everything you do, otherwise you may find that your middle is not necessary everyone's.

![User Stotry to Acceptanc Criteria to Scenario to Feature]({{ site.url }}/assets/img/test-pyramid-details.png)

Meetings where two different groups of interest participate in are on their own very beneficial. You're starting to understand the other group, its problems, issues, expectations, drivers. You learn how it understands User Story, Feature, Scenario, etc. Together you can improve on understanding SCRUM and BDD, and how they complement each other, in order to avoid confusion in future.

### Collaboration on text files

What caught my eye while working on Scenarios is no business friendly editor. You won't find a tool similar to Fitnesse's wiki, where a non-technical person can write and store his scenarios. In BDD you have to work with plain text files. If you want a code highlight or auto-formatting, you need to download a developers' IDE. If you want your changes to be saved, you need to learn SCM, like Git. Not very user friendly... On the bright side people behind Cucumber are working on a web application that will help you with that, it's called Cucumber.pro.

## Pivot

I'm getting somewhere with BDD. It's time for last pivot. Learn more about my final findings in next post.
