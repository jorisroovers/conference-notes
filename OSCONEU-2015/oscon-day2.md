# OSCON EU - Day 2
## Keynote

### AB testing: Test your own hypotheses, and prepare to be wrong

**Stuart Frisby (Booking.com)**


[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46321]()

- Everything they do is based on AB testing
- Why should you be experimenting: "We're normally wrong about what we think is 'good'"
- Why shouln't you be experimenting:
	- you don't have sufficient traffic
	- you success metrics are ill-defined
- Common mistakes with AB Testing
	- Big Shot AB Testing: completely change the page. Problem is that you cannot pick what actually caused the change in user behavior
	- Fringe AB Testing: 
	- Assumed Reproducibility: a change can have widely different results depending on what page it is on
		- "Robbed of context, the result of an experiment is a fart in the wind"
		- Example: hamburger menu. Lot's of opinions, but booking.com's own data showed that it did work for them
	- Hierarchy sources:
		-  your own results > some guys on the internet's opinion
-  AB Testing done right:
	- Test EVERYTHING
	- Test atomically
	- Build your own testing tools: customized to your needs. General tools can never match what you exactly need
	- Build a culture of data-driven product development
	- Hire entrepreneurs

### Privacy: The next frontier

**Ari Gesher (Palantir Technologies)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46011]()

- Sidenote: palantir: [atlasDB](https://github.com/palantir/atlasdb)
	- Transactional Distributed Database layer (ie. ACID on top of NoSQL)
- The architecture of Privacy
	- How to build privacy systems
- Privacy: relatively new concept. Until we had big cities/cameras (1800s), it wasn't really a thing
	- That changed a lot recently: edward snowden/NSA, Google, Facebook, etc
	- Only going to get "worse" with google glass, etc
- New Technology causes new problems
	- Solution is not to undo/get rid of the tech
	- Rather, move forward and fix with: new technology!
	- Tools + incentives = Change	 
- Privacy is not security
	- Similar, not the same
	- Security: AuthC
	- Privacy: AuthZ, access controls
- Privacy
	- Timebased access controls, non-binary access controls (get access to the roles without getting access to the data) 
	- Auditing is also required!
- Defaults matter!
	- A lot of companies don't have time/resources to do privacy well.
	- But we can change that! Call to action!


### Kubernetes: Changing the way we think and talk about computing

**Mandy Waite (Google)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46444]()

- Containers are cool!
- But you run into "how you manage them" very fast!
- Kubernetes: cluster container manager
	- Doesn't schedule containers. It schedules pods, which are a group of containers.
	- Way to describe pods in YAML
	- Kubernetes schedules pods on nodes (=hardware or VMs)
	- Pods have labels: e.g. a certain disk or cpu or something arbitrary you define
	- Scheduler then uses these labels to do the scheduling
	- Scheduler:
		1. Identify node that can satisfy the required labels
		2. Rank them
		3. Choose the best node and run the pod on there
	- Hard part: which to deploy a pod on a node without 
		- Resouce Stranding vs. Efficient Bin-Packing 
- The new language of computers: new way of thinking about computing!
	- Fundamental shift in dealing with computing resources

### Bootstrapping a business around open source

**Ninh Bui (Phusion), Hongli Lai (Phusion)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46067]()

- Phusion: Passenger -> Ruby App OS
- Intrinsic motivation is very important
- 3 lessons:
	- Beware of too much consultancy
		- A way to fund your startup: do consulting on the side
		- Mental overhead is, Loss to context switching!
			- Switching  between client projects and main startup project
			- VC funding not soo bad here
	- Charge actual money for your products
		- How do you make money of of this?
		- Usual answer: provide support contracts!
			- Not so easy: with Passenger people that used it were hackers/developers and generally didn't want/need support
			- Support contract is more like insurance (big companies like banks, governments want this). You also need sales poeple to make that deal.
		- Solution: Passive income
			- Some kind of subscription, recurring income
			- Open source Core. Premium Features as part of subscription.
		- Don't ask for donations!
			- Only works for a very short time. Donations decrease over time. Phsycological thing! 	
		- Don't be afraid to charge for your software. Charging = Future!
	- Market your goods!
		- Word of mouth marketing. Share with everyone and keep sharing.
		- Market the technical details of your work. Hackers like it!
			- Blogposts of technical details keep community involved

### Growth Hacking: Data and Product Driven Marketing

**David Arnoux (Growth Tribe)**

[http://conferences.oreilly.com/oscon/open-source-eu-2015/public/schedule/detail/46945]()

- Growth Hacking: how to keep growing
	- Using unconvential techniques/marketing to attract users
	- People are bombarded with 250-3000 ads per day. Ads don't work to get attention
		- Users have daily life concerns as well. Your ad is just a "blib" in a user's day.  	
- Many examples
- Key behind growth hacking
	- Other People's Network (OPN)
	- To grow, first borrow users from other networks
- So what is Growth Hacking?
	- David vs. Goliath
	- Scientific approach: AB Testing 
		- But also soft data: talk to customers, do user testing
	- Automation! 
- Growth Hacking Principles
	- If you build it, people don't magically come
	- Testing is hugely important: data, data, data!
	- Only continue with successes, kill failures quickly
- Growth Hacker vs. Digital marketer
	- Growth Hacker involved in the whole product, not just the marketing
	- Growth Hacker also well-versed in technology (software developers) 
- Different types of growth
	- Acquisition growth: more users
	- Retention growth
	- Monetization growth
- "Spend 50% of your resources on first user experience"
	- People have expansion span of 5 seconds
- Growth Tribe Academy: learn growth hacking
	- Much more jobs than people how can do it for now!


### OSCON EU: Next year: Oct 17th - Oct 19th: London 


   





