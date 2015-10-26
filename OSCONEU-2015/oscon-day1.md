

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
- Conway's law (communication paths increase exponentially with # of team members)

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










