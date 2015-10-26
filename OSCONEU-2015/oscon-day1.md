

# OSCON EU - Day 1
## Keynote
### The evolution of evolutionary architecture
**Rebecca Parsons (ThoughtWorks)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46066]()

- Enterprise architecture and integration patterns
[http://martinfowler.com/articles/enterprisePatterns.html]()
- Database Migrations
- SOA
	- REST vs. SOAP (REST is more evolutionary)
- Evolvability as first-citizen
- [Conway's law](https://en.wikipedia.org/wiki/Conway%27s_law): (the interface structure of a software system will reflect the social structure of the organization(s) that produced it.
### The Seif Project
**Douglas Crockford (PayPal)**

- Author of Javascript: the good parts
- Seif Project: security project [https://github.com/paypal/seifnode]()
- Multiple Parts
	1. seifnode: crypto services for NodeJS (AES, SHA3, RNG)
		- RNG: based on OS, microphone, camera
	- seif protocol
	- seif Resource Mgmt systems
	- seif Apps: NodeJS + Qt, no HTML
	- embedded seif (seif helper app): in a browser
- Difficulty of software security:
	- Does what it should, doesn't do what it shouldn't

### Docker security 

**Nils Magnus**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46320]()

- Lots of people in the audience have played around with docker, little have it actually deployed in prod
- Let's examine some common threats:
	- **Threat 1**: Complex attack surface
		- Linux containers share a single linux kernel.  these days: kernels exposes over [400 different system calls](https://filippo.io/linux-syscall-table/)
	- **Threat 2**: Insufficient Architecure
	- **Threat 3**: Unauthentic source
		- Dockerhub: hard to verify what containers you download from dockerhub are actually doing
		- Best way to verify this: open source Dockerfile -> you can check the source code
	- **Threat 4**: Turning off security features
		- Docker has number of security features disabled by defaut. E.g.: mounting a filesystem/block device from the host system. => you just opened a backchannel to the host OS.

### Enough Foundations Already! 

**Simon Phipps (Wipro)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46242]()

- Key roles of open source foundations:
  - Main idea: protect the software/community
	1. Asset Lock (patterns, code, etC)
	2. Bank (Money)
	3. Guarantor of Equality
	4. Infra provider
- Self-interest of each participant shouldn't get in the way of the interest of the community.
- Copy-left license probably the best for an OS project...
- Trade Associations (=for the good of the members) vs. Public Benefit (=for the good of the public)
- Trade Associations: hugely expensive and have a set of rules -> everyone "plays"/"game" the rules. THings go bad when the wrong people get in control (e.g. Java: Sun -> Oracle)
- Green Flags for "good" foundations:
	- seperation of responsibilities (tech decisions independent from governance)
	- Public benefit mission
	- OSI-approved license
	- Asset Lock (see before)
	- Representative Governance 
- Want to start a new Foundation -> checklist in slides

### Programming as performance - live coding with Sonic Pi

**Sam Aaron (University of Cambridge)**

- How to make coding/programming more interesting for the general public? Get people excited about code.
- Use music. Sonic Pi -> Music programming using Raspberry Pi
- Sonic Pi: ruby [http://sonic-pi.net/]() 


## Software Architecture as code
**Simon Brown (Coding the Architecture)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/44248]()

- Who likes visio to draw arch diagrams -> no one
- Software architecture -> all about abstraction
-> allows us to reason about complex systems
- Class '4+1' model: to describe an architecture we 
	- Logical view, deployment view, etc.
	- Problem: people use different names for the same thing 
- Retrospective vs. Proactive architecture
- Diagrams vs. Map (e.g. Map of amsterdam)
	- All maps use the same set of abstractions, but use a different set of representations. There is a key that explains the representation.
- Similar to online maps, arch diagrams should be zoomable -> pinch to zoom
- Highest level: people -[interact with]-> software systems
	- Zoom levels: software systems ->  container -> component
- Good book: [Just enough software Architecture](http://www.amazon.com/Just-Enough-Software-Architecture-Risk-Driven/dp/0984618104)
- Diagram Generators suck: they create a mess
- This idea that there is a disconnect between low-level and high-level diagramming has been known for a long time (reference paper of 1995).
- Example of generated diagrams based on Spring's Petstore application
	- First iteration: generate all classes/interfaces -> mess
	- Second iteration: drop utils, entities (=models)
	- Still missing component-level view
- Problem: architecture is not captured in the code
- Possible solution: architecture description languages -> textual representation of architecture that cna then be rendered
	- Exists for a long time, but mostly academic -> nobody is really using it
	- Then manage this textual description in git
- Can we scrape some of the high-level info from the source code?
	- No. You can try some things (e.g. look for API endpoints, look for libraries), but these are all implicit, very very hard if not impossible to get good abstractions
	- This is true at various levels: people, software systems, containers, components
-  Architecture evident coding stle
	- Use of annotations, attributes, naming conventions, namingspacing, packages, modules
	- Then higher-level of abstractions can be derived from the codebase.
- Leads to: DSL (domain specific language) to describe architecture in code
- example of DSL written in Java 
-> structurizr: [https://www.structurizr.com/](), [https://github.com/simonbrowndotje/structurizr-java-example]()


## Chaos patterns - architecting for failure in distributed systems ##

**Jos Boumans (Krux Digital), Bruce Wong (Twilio)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/44442]()

- Experience from companies: Krux, Netflix, Twilio
- Example: AWS DynamoDB failure (sept 20th, 2015)
	- Terms: [https://en.wikipedia.org/wiki/Thundering_herd_problem](thundering herd),  
	- Cascading failure: a lot of other products depend on DynamoDB: monitoring, alerting, autoscaling -> everyhing failed
	- "No paddle, sh*t creek"
- This is just a single instance.
- Problem: distributed systems are very complex and can't be simulated because they are so large. A certain set of problems only occurs on very large scale systems.
- One solution is to be agile: different process -> deploy small changes all the time -> become more confident and minimize risk
- Systems still can fail. You should consider resilience to be a feature => embrace failure. 
- Case Study: Twitter
	- Core experience: tweets + Optional enhancements
	- If optional enhancements 
- Build in fail-safes:
	- Fallback patterns:  
		- If the DB is down, can you use the cache copy?
		- If the API is, can you're front-end cope with it? e.g.: use a CDN 
		- Use CDN is down: use local device cache?
		- API: Instead of failing when the app server can't reach the DB, return a 200/OK suggesting that another approach needs to be taken
		- CAP Theorem: You can't have Availability, Consistency and Partition Tolerance at the same time
			- Different systems are better at different things. General guideline (except for medical/financial systems): use eventual consistency
	- Split out your control plane (avoid cascading failures):
		- AWS: Use some of their services like DyamoDB, but use other services for control plane so that when AWS goes down, at least you're control plane doesn't go down.
		- Avoid cross region dependencies
	- Example: User experience: Twitter
		- When you hit "post", what happens? Is it send directly to the server, does it happen async after the UI has been updated? What if the users refreshes the page right after clicking post? -> 	 

- **Chaos Engineering**: how do we know that the product degrades does like it needs to without having it an actual outage
	- How confident are you? Now? Tomororw? Next week? After a patch? vs. "If it ain't broke don't fix it"
	- Chaos engineering is about building confidence
		- Outages: uncontrolled, unpredictable, unintented -> large impact 
		- Chaos: controlled, planned, intentional, microscopic user impact
	- How do you discover Single Point of Failures (SPOF)?
		- How do you validate that you've fixed a SPOF? -> you need to validate very often
	- Chaos Monkey: SPOF detector
		- Kills servers randomly, but only runs during business hours so team can respond when something goes wrong
		- Maybe not do it during product launch either...
		- "Failure Fridays": certain companies kill random servers on friday afternoon -> helps developers	to be proactive
	- SLOW is hard. Make production + business + engineering decisions. When the short-cut slow operations? Twitter example: better to short-cut loding trends and not showing them, then to load everything slowely.
		- Latency Monkey, other frameworks
	- "Chaos is a dial, not a switch": you don't turn it on or off, you dial it to gradually introduce more chaos. Start small!
	- Region failures:
		- Chaos Kong: similutates region failures
		- How to fix: GeoDNS (fallback to LatencyDNS), Proxy (cross region communication), Capacity (making sure you have enough capacity in other regions to cope with a region failover. If you're not careful you might create a cascading failure by overloading a healthy region during a failover).
- Key takeaways:
	- Failure will happen ("Once in a blue moon" happens few times a year) 
	- Go found Chaos Engineering in your company!
- Q&A:
	- How do you have your engineers do this: "Chaos/Failure driven development", similar to "Test driven development"
	- If you use a different service for monitoring (e.g.: New Relic, PagerDuty), don't they rely on AWS as well?
		- They often do to some extent, this is tricky...

## Building microservices with Go

**Baron Schwartz (VividCortex)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/43895]()

- Before Talk Q: How big to make a microservice?  A: Hard to answer. Don't take it too far. Microservice should consist of related functionality (e.g. metric, data collection, etc). 1 example: Create different read and write paths for your app (i.e. different microservice for read than for write) because those things have very different requirements.
-  VividCortex: 250 repos, 30 engineers
-  Separating reads from writes. LB using HaProxy, Nginx. Note that it might be a single binary, but just deployed twice: one handling reads, one handling writes.
-  Problem: code duplication across micro-services. Initial solution: created an internal REST framework: NAP (a NAP is a small REST :-)).
-  NAPv3: [Siesta](https://github.com/VividCortex/siesta)
	- No batteries included
	- Yes, there are a bunch of other Go web frameworks ([Gin](http://gin-gonic.github.io/gin/), [Martini](https://github.com/go-martini/martini)
- Dependency management in Go: problematic, community still hasn't set on a solution. Baron's solution: custom perl script
- Continuous Deployment: CircleCI, Hubot, 
	- [Travis vs. CircleCI](https://strongloop.com/strongblog/node-js-travis-circle-codeship-compare/)
- [12-factor apps](http://12factor.net/)
	- Do not deamonize, use [runit](http://smarden.org/runit/)
- dependency management: when updating a library, all services needs to be updated.
- Use of Kafka
- PM: [Process Manager across different microservices](https://github.com/VividCortex/pm)


## GET /better

**Mark Bates (Meta42 Labs, LLC)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/42653]()

- Long inspirational story about how Mark grew up.
- 5 Tips:
	1. Practice: code every day
		- How to? Always be coding
			- Contribute
			- Build
			- How to get ideas: copy existing ideas
				- Copy twitter, copy facebook, copy ...
	2. Share
		- github!
		- Open source code at your own projects/work code
		- Fix issues in library
		- When contributing to other code: you're forced to adopt other people's style and libraries
		- It helps build your name
	3. Blog/Write
		- Helps to improve your communication skills
			- Hiring managers love this!
			- Similarly: write documentation
		-  Tough at first, but try make it a habbit
	4. Perform
		- Speak at conferences
		- Travel, free beer :-)
	5. Network
		- Hugely important
		- Introvert vs. Extravert. Even if it takes a lot of energy out of you, still do it, even if you need some "me"-time later. It's worth it!

**Q&A**: How do you balance continously getting better with burning out? A: Take breaks if needed, but also make sure you love what you are doing. If you are burning out, then it is often a sign that you aren't doing what you love.




## Perl 6 for mere mortals

**Curtis Poe (All Around The World)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/42812]()

- Perl 6 is NOT the next version of Perl
	- Perl 6 is separate from Perl 5 the same way C# and Java are different
- Why Perl 6? Focus on "The Big 3"
	- Useful Types
- We won't be looking at perl in depth, more at the high level
- Math: 7/2, -7/2, .1 + .2 + -3.
	- Most languages give incorrect results, Perl 6 actually gives the correct result
- Basic Function Signatures
```
sub fib($nth) {
	given $nth {
	when 0 { 0 }
	when 1 { 1 }
	default { fib($nth-1) + fib($nth-2) }
}
```  
- No return statement required in Perl. It could be there, but it's optional. In case it's not specified, the last evaluated value is returned (in this case: ```fib($nth-1) + fib($nth-2)```.
- Function parameters: optional type hinting available, but also more advanced constraints like: string must be < 256 chars
	- Type hints evaluated at compile time. Wrong type -> compiler errors
	- Constraints: evaluated at run time 
- Concurrency: switching between jobs <-> Parallelism: throughly running in parallel
- Presenter had to skip very fast through types, classes because of time.
- Summary
	- Math that works
	- Powerful function signatures
	- Types you can actually yes
	- Powerful, expressive classes





