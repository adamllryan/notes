Common interview categories:
# Behavioral Questions
Behavioral questions commonly assess the following: 
- Leadership skills - What experience do you have leading teams and how do you go about doing so?
- Problem solving skills - How well do you handle problems and what is your process through working through them?
- Teamwork experience - How well do you perform in team settings and how much experience do you have doing so?
# Technical Questions
This has many more categories within it, including the following: 
- What experiences do you have with programming languages?
- How well do you understand object-oriented programming and how would you use it to approach something?
- Can you solve this algorithms problem?
- Job-specific technical questions. Such as front/back-end experience, Agile, SDLC, SQL, Databases, Network/Systems Administration, Cloud and Devops, etc. 

Common languages may include C/C++/C#, Java, Python, SQL family, Assembler, JavaScript, Ruby, etc. 

Object Oriented Programming (**OOP**) is built upon the following pillars:
- **Inheritance**, which is where objects inherit from parent classes and interfaces
- **Polymorphism**, where we focus on static overloading and dynamic overriding
- **Abstraction**, which is the idea of defining structure without features, or method without code in a nutshell
- **Encapsulation**, where we hide the implementation to outsiders. We want to be able to understand the method names only, not how they work

The Software Development Lifecycle (**SDLC**) is intended to produce high-quality software with low cost and little time. The cycle consists of the following phases:
- *Plan* - Resource Allocation, Capacity Planning, Project Scheduling, Cost Estimation, Provisioning
- *Code* - System Design in IDE, Static Code Analysis, Code Review
- *Build* - Build Project with Code Requirements from above
- *Test* - Evaluate product, Assess, Unit Testing, Code Quality Testing, Integration Testing, System Testing, Security Testing, Performance Testing, Acceptance Testing, Nonfunctional Testing
- *Release* - Team Packaging, Managing/Deploying Releases across different environments
- *Deploy* - Release into production environment
- *Operate* - Software use in production environment
- *Monitor* - Evaluate software, System Performance, User Experience, Security Vulnerabilities, Analysis of bugs and errors

The **Agile** Manifesto defines the following priorities:
- Individuals and Interactions over processes and tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

In backend work, we use the RESTful interface, which lets us send JSON objects to and from end machines. (GET,PUT,POST,DELETE)

Important SQL concepts may include: 
- Queries, be able to develop queries
- Keys, understand the types of keys
- Joins, know the difference between inner and outer joins (and types of outer joins)

When approaching a coding problem, follow these steps:
1. Articulate the problem (repeat it back)
2. Confirm any assumptions or questions (make sure you understand)
3. Ask for examples or what the results of those examples would be
4. Develop a high level English solution
5. Rewrite that solution in pseudocode and produce a Big O complexity
6. Implement your solution
7. Test

Common sorting algorithms you WILL need to know are quick sort and merge sort. We need these because they both have $\Theta(n\text{log(n)})$ expected time complexity. 
Quick sort is $O(n^2)$. 
1. Choose a pivot. I learned to choose it randomly, but you can do start or end as well. 
2. Iterating from left to right, find something larger and smaller than the pivot (that are out of order) and then swap them. 
3. Move pivot to correct spot and repeat. 
Merge sort is $O(n\text{log}(n))$. 
1. Recursively split the array in half until we cannot anymore. 
2. Sort each and merge repeatedly until we are back. 
3. Complete!

Normally, we will choose quick sort because it has a smaller space complexity. 