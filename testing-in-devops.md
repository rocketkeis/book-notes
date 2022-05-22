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

* Agile Testing: A Practical Guide for Testers and Agile Teams by Lisa Crispin & Janet Gregory
* More Agile Testing: Learning Journeys for the Whole Team by Lisa Crispin & Janet Gregory
* Growing Agile: A Coach’s Guide to Agile Testing by Samantha Laing & Karen Greaves

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
—Elisabeth Hendrickson, *[Explore It!](https://pragprog.com/book/ehxta/explore-it) Reduce risk and increase confidence with exploratory testing*

Deployment pipelines are well-known and have been part of the agile testing approach for many years. The abstract from Jez Humble and David Farley’s book *[Continuous Delivery: Anatomy of the Deployment Pipeline](http://www.informit.com/articles/article.aspx?p=1621865&seqNum=2)* is a useful starting point if the concept is new to you.

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

This section explains three common practices for testing in production:

| Name                    | Description |
|-------------------------|-------------|
| A/B testing             | Use a controlled experiment to present two versions of your software to your users to see which one they prefer
| Beta testing            | Release a new version of your software to a subset of users to determine its readiness for a wider audience
| Monitoring as testing   | Use production monitoring to identify when problems happen and to confirm when they are fixed

**Limitations of A/B testing**

There’s the well-known example of how Google used A/B testing to determine which shade of blue to use on their toolbar. They tested 41 gradients to learn the colour people preferred, which was seen by some as a trivial attribute to experiment with.

A/B testing should not become the only way to make a decision. If you start to defer every decision to your user, you remove autonomy from the development team...  There is a famous quote often misattributed to Henry Ford: “if I had asked people what they wanted, they would have said faster horses.”

**Limitations of beta testing**

Brian Marick cautioned against an overreliance on beta testing in his 1997 paper titled [Classic Testing
Mistakes](http://www.exampler.com/testing-com/writings/classic/mistakes.html). He listed five problems with beta testing that can be summarised as:
1. If beta testing is optional, the users who self-select will not be representative of all users. There will be a skew towards early adopters of new technology, who will have different expectations to a pragmatist who waits to adopt until after the technology is proven.
2. Beta testers may only do a quick tour of the product rather than a deep exploration, which will leave problems undiscovered.
3. Usability problems may not be reported, as beta testers could be uncertain about whether these are important.
4. Beta testers may not report all the bugs that they observe, especially if they’re not sure what they did to cause the problem.
5. The bug reports of beta testers are often difficult to interpret and it may require a lot of effort to identify the root cause.

Beta testing may not suit DevOps, as it best suits organisations with relatively infrequent releases.

Google are well known for running lengthy beta programs. Gmail, was labelled as beta for five years
from 2004 to 2009.

[Should Tesla be 'beta testing' autopilot if there is a chance someone might die?](https://www.theguardian.com/technology/2016/jul/06/tesla-autopilot-fatal-crash-public-beta-testing

**Monitoring as testing**

You can use production monitoring to identify when problems happen and to confirm when they are fixed, as an alternative to testing before release. This practice is called ‘monitoring as testing’.

He \[Ed Keyes\] [advocated for monitoring](https://www.youtube.com/watch?v=uSo8i1N18oc) that included functional verification and log message analysis, used to detect problems related to two types of input:
1. User events. Treat every interaction as a test case that “you didn’t have to think of and maybe wouldn’t have”.
2. Automated tests. Run targeted, scripted actions against the production environment regularly.

Rather than monitoring *as* testing he \[Leon Fayer\] [advocated for monitoring *and* testing](https://www.youtube.com/watch?v=VIhIm5kEWFg). Leon positioned monitoring as a component of test strategy to help discover “unknown unknowns”.

**Exposure control**

Exposure control is controlling the introduction of new software to users to limit the exposure of the organisation that has written the software.

*\[KC: I found this part interesting. Because among the terms introduced, I'm only familiar with the term "dogfooding"\]*

“**Canary release** is a technique to reduce the risk of introducing a new software version in production by slowly rolling out the change to a small subset of users before rolling it out to the entire infrastructure and making it available to everybody.” —Canary Release, Danilo Sato

Cloud Foundry use an open-source tool chain called BOSH for releases, which uses automatic canaries by default. The tool applies changes to one server first, then verifies the outcome of the changes before continuing.

A **staged rollout** is a canary release with a different focus. Instead of creating a canary by limiting changes to infrastructure, the rollout intentionally limits the number of users with access to the new code. Both methods allow a smaller initial release that can help to discover problems.

*\[KC: Just like updates on Instagram\]*

**Dogfooding** is where the people who write the software are the first to use it:

**Dark launching** Instead of creating a small release to validate new software, it implements the new code but in a way that it is not visible to the user. This allows new code to be executed and monitored alongside the old code.


## Testing in DevOps Environments










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
* Link to Jez Humble and David Farley's *[Continuous Delivery: Anatomy of the Deployment Pipeline](http://www.informit.com/articles/article.aspx?p=1621865&seqNum=2)*
* [Feature toggles](https://martinfowler.com/articles/feature-toggles.html) and content on testing a toggle
* Bug bash and examples/links of different approaches

### Testing in Production

* Sections on testing monitoring, analytics and logging
* "There's the well-known example of how Google used A/B testing to determine which shade of blue to use on their toolbar. They tested 41 gradients to learn the colour people preferred, which was seen by some as a trivial attribute to experiment with."
* "Google are well known for running lengthy beta programs. Gmail, was labelled as beta for five years from 2004 to 2009."
* [Should Tesla be 'beta testing' autopilot if there is a chance someone might die?](https://www.theguardian.com/technology/2016/jul/06/tesla-autopilot-fatal-crash-public-beta-testing)
* TIL *passive* validation. Differences were explained by Seth Eliot in [Testing in Production (Vimeo link)](https://vimeo.com/64786696).
* The terms to describe variations of exposure control such as canary release, staged rollout, dogfooding, and dark launching

### Testing in DevOps Environments
