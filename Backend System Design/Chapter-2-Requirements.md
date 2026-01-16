### Identify Requirements
- Core elements of system design
	- Translating business requirements.
	- Designing API and architecture.
	- Understanding technology and trade offs
- Building ToDo app: Question to be asked:
	- What core feature do we need to support
		- Strategy:
			- Scope the problem (how many user are going to use, is it a mobile app or web app, etc).
			- Design the high-level architecture
			- Address key challenges and trade-offs.
		- **Understanding the problem:**
			- Always ask question don't make assumptions
			- Functional Requirements: (what is the function, what the core of the app)
				- What are the requirements.
				- Functional requirements are 2 parts
					- **Functional:** Describe **<u>what</u>** the system should Do
					- **Non-Functional:** Describe **<u>how</u>** the system should perform.
				- What are the core features?
					- what should users be able to do?
				- Who are the users?
					- Are there different types of users?
				- How do users interact with the system?
					- What devices are supported
				- Are there edge cases to consider?
				- What are the constraints?
				- Is the application read heavy or write heavy (for CRUD based)
			- **Example:** Functional Req of Pizza shop
				- User should be able to view the menu of pizza and toppings.
				- User should be able to order a pizza.
				- User can only order 1 pizza at a time.
				- There is only 3 sizes of pizza.
				- A pizza can have at most 3 toppings.
- Questions:
	- What are the four main elements of good system design, in order of priority?
		- The four main elements are: 
		1) Translating business requirements, 
		2) Designing the API and architecture, 
		3) Handling edge cases and making trade-offs, and 
		4) Understanding the actual technology. Translating business requirements is the most crucial first step.
	- What is the difference between functional and non-functional requirements in system design?
		- Functional requirements describe what a system can do - the features, user interactions, and business requirements. Non-functional requirements describe how the system should perform - the quality attributes like speed, consistency, and performance trade-offs that constrain the system.
	- What is the recommended time allocation strategy for a one-hour system design interview?
		- The recommended allocation is: 10-15 minutes for scoping, 20-30 minutes for high-level architecture, and 15 minutes for trade-offs discussion. Scoping is the most important part and should not be rushed or skipped.
	- What are essential scoping questions to ask when designing a system?
		- Essential scoping questions include: How many users will use the system? Who are the users and what are their skill levels? What devices will users interact with? Are there different types of users with different permission levels? What are the core features versus nice-to-have features? What constraints is the system operating under?
***
### Functional Requirements Exercise: Bank
- You're designing a mobile banking application that allows users to manage a single bank account.
- What are the question you might ask?
- What are examples of functional requirements?
- **Questions:**
	- What types of transactions should the app support (deposits, withdraw, transfers)?
	- How far back does the history need to go?
	- What level of detail does the transaction need to have?
	- what level of security do we need to have?
	- How do we invalidate session / load a user out?
	- Is there compliance we need to adhere to?
	- What are the performance requirements?
	- How do we display transaction status?
	- What types of notifications do we show / send the user?
	- What is the primary device type for users (Android / Iphone).
	- Do we have to support mobile wallets?
- **Functional:**
	- Users should be able to login to their account with a username and password
	- User should be able to export transaction data from the past 12 months.
	- Users are required to setup MFA
	- Users should be able to transfer, receive money and schedule transfers.
	- User should be able to report fraud.
	- Users should be able to search and filter history
	- Users should be able to categorise transactions for budgeting.
	- What currency is supported (INR for India).
	- Users should get insufficient balance message if balance <= 0.
	- How transactions should be presented like datetime, amount, status.
	- All datetime should be localised.
	- User are located in the India
***
### Functional Requirements Exercise: URL Shortener
- You're designing a service that converts long URLs into shorter, more manageable links.
- **Questions:**
	- Can users customise the shortened URL.
	- Can users also generate the QR for shorten URL
	- If any user clicking on the shorten link do we have to show the where he is going to be redirected page for avoiding phishing attacks?
	- Any rate-limiting on creation and click-ability of the shorten URL.
	- Is there a limit on urls created per user?
	- Can URLs Expire?
	- Are there different levels of users (paid tier)
	- Are URLs limited to HTTP/HTTPS.
	- Do we need analytics on the links?
	- Do users need to create accounts to make shortlinks
- **Functional:**
	- User should Able to login to their accounts with a user name and a password.
	- Logged in user should be able to create, edit and delete the URLs.
	- Visiting Users can report any shorten URL as a phishing.
	- User should be able to convert long URLs into shorten version.
	- Free users expire after 6 months.
***
### CAP Theorem
- The System should be:
	- Reliable
	- Availability
	- Resiliency (How well system handles failures)
	- Consistency (users sees the same data at the same time)
- CAP = Consistency, Availability and Partition Tolerance
	- **Consistency:** Every read receives the most recent write or error.
	- **Availability:** Every request receives a (non-error) response
	- **Partition Tolerance:** The system continues to operate even if messages are delayed or lost.
- But in Distributed Systems we can only get 2 of the 3 CAP only:

| Pick Two | Trade Off                                              | Reality  |
| -------- | ------------------------------------------------------ | -------- |
| C + A    | Only works without network issue                       | Not sure |
| C + P    | Always show the latest data but unreliable performance | Yes      |
| A + P    | Always responds but might show outdated data           | Yes      |
***
### System Quality
- Reliablity
	- Availability
	- Resiliency (Partition Toloerance)
	- Consistency
- Observability: The ability to know what is happening in your system (metrics).
- Security: The ability to safeguard your system and its data.
- Scalability: The ability handle increases or decreases in system usage.
- Adaptability: The ability to handle changing requirements or user behaviours.
- Performance
	- Latency: How quickly does the system responds
	- Throughput: How much data can move through the system at a given time
***
### Non-Functional Requirements
- How many users do we expect?
	- What is the average RPS (Request per second)?
	- Does this number change over time
- How consistent does the system needs to be?
	- Is it acceptable for users to see sightly outdated data?
- What metrics are important?
	- What is the maximum latency?
- What data need to be protected?
***
### Non-Functional Requirements (banking app)
- **Questions:**
	- How many MAU's?
	- How many transactions per user?
	- How frequent are the transactions?
	- How long do we store transaction data?
	- What is the minimum latency for a transaction?
	- What is our availability target?
	- How consistent are the traffic patterns?
- **Non-Functional**
	- 