# A Practical Guide to Testing in DevOps

A Practical Guide to Testing in DevOps (2017)
By Katrina Clokie


## Preface

Wikipedia defines DevOps as:
> **DevOps** (a clipped compound of development and operations) is a term used to refer to
a set of practices that emphasizes the collaboration and communication of both software
developers and other information-technology (IT) professionals while automating the
process of software delivery and infrastructure changes. It aims at establishing a culture
and environment where building, testing, and releasing software can happen rapidly,
frequently, and more reliably.

*\[KC: I hear [Henry Cavill](https://www.youtube.com/watch?v=pBiU7zf2N1o).\]*


## Testing in a DevOps Culture

*\[KC: Interesting. Test strategy retrospective.\]*

In a cross-functional team where anyone can perform testing, it is important to have a shared understanding of both the practical approach to testing tasks and the underlying test strategy. Agreement about the test activities means any person who picks up a testing task understands the wider context in which they operate. This helps them understand the boundaries of their task: what they should test and what sits within another activity.

[Assessment - How agile is your testing?](http://www.growingagile.co.za/2015/10/assessment-how-agile-is-your-testing/)

Score 1 point for each statement that is TRUE
1. The whole team is clear on what should be tested for each story and feature before any coding starts.
2. Before you discuss the solution, you make sure you understand the who and why behind any requirement.
3. You ask, and answer the question “How will we test that?” when discussing a user story.
4. Everyone on the team knows how to run the automated tests and read the results.
5. You discuss what you will automate at which level so that you don’t duplicate tests between the unit, component and UI levels.
6. Your test scripts are version controlled and labelled along with the source code, since tests are part of the working software.
7. You don’t have a bug database because you fix bugs as soon as you find them, instead of logging them.
8. When your continuous integration server fails, it is addressed and returned to a working state within an hour.
9. When observing your standup meeting an outsider would not be able to tell who is a developer and who is a tester.
10. Your team has a way to measure quality, which you use to identify if your testing process is working for you.

If your team scored less than five, you may find these books useful:

* Agile Testing: A Practical Guide for Testers and Agile Teams14 Lisa Crispin & Janet Gregory
* More Agile Testing: Learning Journeys for the Whole Team15 Lisa Crispin & Janet Gregory
* Growing Agile: A Coach’s Guide to Agile Testing16 Samantha Laing & Karen Greaves

*\[KC: There's mention of the two pizza rule. But I guess it depends on where you're ordering from, and the size. I can easily eat a whole pizza by myself.\]*

**Blazing a trail** When I’m blazing a trail I’m building a path to someone new in the organisation.

Ioana \[Serban\] talks about the "Three Little Questions" that she uses for building individual relationships between testing and operations:
1. What are you working on?
2. Want to see something cool?
3. Can you pair with me on this?

Regularly practicing how to explain what you are doing can make it much easier to repeat this information to a person beyond your development team.

I have published a number of illustrated blog posts that give practical examples of applying visualisation when testing a product:
* [Visual Test Ideas](http://katrinatester.blogspot.co.nz/2014/11/visual-test-ideas.html)
* [Visual Test Models & State Transition Diagrams](http://katrinatester.blogspot.co.nz/2015/01/visual-test-models-state-transition.html)
* [Evolution of a Model](http://katrinatester.blogspot.co.nz/2014/04/evolution-of-model.html)
* [Three examples of context-driven testing using visual test coverage modelling](http://katrinatester.blogspot.co.nz/2014/10/three-examples-of-context-driven.html)

[...a pairing experiment for sharing knowledge between agile teams...](http://katrinatester.blogspot.co.nz/2015/06/a-pairing-experiment-for-sharing.html)
People who are unfamiliar with pairing may be a little hesitant to try it. But if you’ve created and fostered a connection with someone, they’ll probably be willing to spend an hour to give something new a try. If it works, you’ve found a new way to share ideas across disciplines. If it doesn’t, the cost is limited.


## Testing in Development

“We always find the most serious bugs when we go off the script”
—Elisabeth Hendrickson, *Explore It! Reduce risk and increase confidence with exploratory testing*

Deployment pipelines are well-known and have been part of the agile testing approach for many years. The abstract from Jez Humble and David Farley’s book [Continuous Delivery: Anatomy of the Deployment Pipeline](http://www.informit.com/articles/article.aspx?p=1621865&seqNum=2) is a useful starting point if the concept is new to you.

A feature toggle is a configuration option that defines whether or not a feature within your software should be executed. You might also hear this concept called feature flags, flippers, switches, feature bits, or latent code.

A bug bash is an activity where all the people involved in the delivery of software put aside their
usual work and participate in a dedicated testing session

* [Experiences of a Testing Bug Bash](http://stephenjanaway.co.uk/stephenjanaway/experiences/experiences-testing-bug-bash/) - Stephen Janaway
* [Bug Bash: The Game](http://www.testingtrapezemagazine.com/wp-content/uploads/2016/12/TestingTrapeze-2016-December-v2.pdf) - Theresa Neate
* [How to run a bug bash](http://scottberkun.com/2008/how-to-run-a-bug-bash/) - Scott Berkun


## Testing in Production

There are a number of different practices that fall under the banner of testing in production: A/B testing, beta testing, and monitoring as testing. The success of each relies on established communication paths between development and operations.

Effective Monitoring & Alerting - Slawek Ligus
> “*Monitoring* is the process of maintaining surveillance over the existence and magnitude of state change and data flow in a system. Monitoring aims to identify faults and assist in their subsequent elimination. The techniques used in monitoring of information systems intersect the fields of real-time processing, statistics, and data analysis. A set of software components used for data collection, their processing, and
presentation is called a monitoring system.
>
> *Alerting* is the capability of a monitoring system to detect and notify the operators about meaningful events that denote a grave change of state. The notification is referred to as an alert and is a simple message that may take multiple forms: email, SMS, instant message (IM), or a phone call. The alert is passed on to the appropriate recipient, that is, a party responsible for dealing with the event. The alert is often logged in the form of a ticket in an Issue Tracking System (ITS), also referred to simply as ticketing system.”

Analytics refers to the data we collect about our users’ activity with our product. In a web application this might be page views. In a telephone network it might be call durations. In a banking product it might be transaction volumes. Organisations collect all sorts of data to learn about their users’ behaviour and respond to it.

He \[Matthew Skelton\] suggests concentrating testing of log files on these three points \[[Why and how to test logging](https://www.infoq.com/articles/why-test-logging)\]:
1. Events that we expect to occur appear correctly in the log stream
2. Transaction identifiers (aka correlation IDs) flow through the log stream as expected
3. Events are logged at the appropriate level (Info, Error, Debug, etc.) if we’re using configurable log levels

This section explains three comon practices for testing in production:

| Name                    | Description |
|-------------------------|-------------|
| A/B testing             | Use a controlled experiment to present two versions of your software to your users to see which one they prefer
| Beta testing            | Release a new version of your software to a subset of users to determine its readiness for a wider audience
| Monitoring as testing   | Use production monitoring to identify when problems happen and to confirm when they are fixed



## Stuff I found interesting, or could come in handy

### Testing in a DevOps Culture

* Test strategy retrospective
* Agile assessment [How agile is your testing?](http://www.growingagile.co.za/2015/10/assessment-how-agile-is-your-testing/)], and book recommendations if you scored less than five out of ten
* Two pizza rule for team sizes - Found this interesting because depending on the restaurant and the size, I can easily eat a whole pizza by myself.
* Blazing a trail - "When I’m blazing a trail I’m building a path to someone new in the organisation..." This isn't limited to DevOps; feels relatable as we're building the local practice and the CoP.
* Ioana Serban's "Three Little Questions" from [TestOps: Chasing the White Whale (YouTube video)](https://www.youtube.com/watch?v=I6A07ESTc_k)
* Links to blog posts of applying visualization when testing a product
* [Pair testing experiment framework](http://katrinatester.blogspot.co.nz/2015/06/a-pairing-experiment-for-sharing.html)
* Dojos - This just makes me want to google if there are testing dojos as there are coding dojos.

### Testing in Development

* Link to Elisabeth Hendrikson's *[Explore It!](https://pragprog.com/book/ehxta/explore-it)*
* Link to Jez Humble and David Farley's [Continuous Delivery: Anatomy of the Deployment Pipeline](http://www.informit.com/articles/article.aspx?p=1621865&seqNum=2)
* [Feature toggles](https://martinfowler.com/articles/feature-toggles.html) and content on testing a toggle
* Bug bash and examples/links of different approaches


## Testing in Production

* Sections on testing monitoring, analytics and logging
