# Software Engineering Fundamentals – Complete Notes

## 1. What is Software Engineering?

**Definition:** Software Engineering is a systematic approach to designing, developing, testing, deploying and maintaining software applications.

Simple words: Software ko proper planning, coding, testing aur maintenance ke through develop karna Software Engineering kehlata hai.

### Objectives

- High-quality software develop karna.
- Software reliable aur secure banana.
- Development cost reduce karna.
- Time par project complete karna.
- Software ko maintainable aur scalable banana.

### Characteristics of Good Software

1. Reliability – Software correctly work kare.
2. Maintainability – Easily update aur fix ho sake.
3. Efficiency – Resources ka proper use kare.
4. Usability – User-friendly ho.
5. Security – Data aur system protected rahe.
6. Scalability – Increased users/load handle kar sake.
7. Portability – Different platforms par run ho sake.

---

## 2. Software Development Life Cycle (SDLC)

**Definition:** SDLC is a structured process used to develop software from initial planning to final maintenance.

### 7 Phases of SDLC

1. Planning – Project ka goal, budget aur timeline decide karna.
2. Requirement Analysis – Client ki requirements understand karna.
3. Design – Software architecture, database aur UI design karna.
4. Development – Actual coding karna.
5. Testing – Bugs aur errors identify karna.
6. Deployment – Software ko production environment mein release karna.
7. Maintenance – Updates, bug fixes aur improvements karna.

### SDLC Flow

Planning → Requirement Analysis → Design → Development → Testing → Deployment → Maintenance

### Advantages

- Structured development.
- Better project management.
- Reduced development risks.
- Improved software quality.

### Interview Question

**Q. What is SDLC?**

SDLC is a systematic process that defines different phases of software development, including planning, analysis, design, coding, testing, deployment and maintenance.

---

## 3. Software Development Models

Development models define how software development activities are organized and performed.

### 3.1 Waterfall Model

Waterfall is a linear and sequential software development model.

Each phase must be completed before moving to the next phase.

**Flow:** Requirements → Design → Coding → Testing → Deployment → Maintenance

Advantages:

- Easy to understand.
- Simple project management.
- Clear documentation.

Disadvantages:

- Difficult to change requirements.
- Testing happens relatively late.
- Not suitable for frequently changing projects.

**Best for:** Projects with fixed and clear requirements.

### 3.2 Agile Model

Agile is an iterative and incremental software development approach.

Software is developed in small cycles, and feedback is collected continuously.

Advantages:

- Flexible requirements.
- Continuous feedback.
- Faster delivery.
- Better teamwork.

Disadvantages:

- Requires continuous communication.
- Difficult to predict exact cost and timeline.
- Requires active customer involvement.

**Best for:** Projects where requirements change frequently.

### 3.3 Spiral Model

Spiral Model combines iterative development with risk analysis.

Each cycle includes:

1. Planning.
2. Risk Analysis.
3. Engineering.
4. Evaluation.

Advantages:

- Strong risk management.
- Suitable for large projects.
- Supports changing requirements.

Disadvantages:

- Expensive.
- Complex to manage.
- Requires risk-analysis expertise.

### 3.4 Prototype Model

A preliminary working version of software is created to understand user requirements.

Advantages:

- Better requirement understanding.
- Early user feedback.
- Helps identify missing features.

Disadvantages:

- Can increase development time.
- Users may confuse prototype with final product.

### 3.5 V-Model

V-Model is also called Verification and Validation Model.

Each development phase has a corresponding testing phase.

Example:

- Requirement Analysis ↔ Acceptance Testing.
- System Design ↔ System Testing.
- Architecture Design ↔ Integration Testing.
- Module Design ↔ Unit Testing.
- Coding is at the bottom of the V.

### Important Comparison

| Model     | Main Feature                        |
| --------- | ----------------------------------- |
| Waterfall | Sequential development              |
| Agile     | Iterative development               |
| Spiral    | Risk-based development              |
| Prototype | Early working model                 |
| V-Model   | Development + corresponding testing |

---

## 4. Software Requirements

Requirements define what a software system should do and how it should perform.

### 4.1 Functional Requirements

Define WHAT the system should do.

Examples:

- User login.
- User registration.
- Password reset.
- Payment processing.
- Search functionality.

### 4.2 Non-Functional Requirements

Define HOW WELL the system should perform.

Examples:

- Performance.
- Security.
- Reliability.
- Scalability.
- Usability.
- Availability.

### Difference

| Functional              | Non-Functional         |
| ----------------------- | ---------------------- |
| Defines system features | Defines system quality |
| What system does        | How system performs    |
| Login functionality     | Login response time    |
| Payment processing      | Payment security       |

### 4.3 SRS (Software Requirement Specification)

SRS is a document that describes the complete requirements of a software project.

It includes:

- Introduction.
- Project scope.
- Functional requirements.
- Non-functional requirements.
- System constraints.
- External interfaces.
- Assumptions and dependencies.

**Importance:** SRS acts as an agreement between client and development team.

---

## 5. Software Design Fundamentals

Software Design defines the architecture, components, interfaces and data flow of a software system.

### 5.1 High-Level Design (HLD)

HLD describes the overall system architecture.

Includes:

- System architecture.
- Major components.
- Database selection.
- Technology stack.
- Communication between modules.

### 5.2 Low-Level Design (LLD)

LLD describes the internal implementation details of individual components.

Includes:

- Classes and objects.
- Functions and methods.
- Database schemas.
- Algorithms.
- Detailed logic.

### HLD vs LLD

| HLD                  | LLD                       |
| -------------------- | ------------------------- |
| Overall architecture | Internal component design |
| Big-picture view     | Detailed implementation   |
| Modules and services | Classes and methods       |
| System-level design  | Component-level design    |

### 5.3 Modularity

Breaking a large software system into smaller independent modules.

Benefits:

- Easy maintenance.
- Code reusability.
- Easier debugging.
- Better organization.

### 5.4 Cohesion

Cohesion describes how closely related the responsibilities of a module are.

**High Cohesion is desirable.**

Example: A payment module should focus mainly on payment-related operations.

### 5.5 Coupling

Coupling describes the dependency between different modules.

**Low Coupling is desirable.**

Example: Changing one module should not unnecessarily break another module.

**Remember:**

- High Cohesion = Good.
- Low Coupling = Good.

---

## 6. Software Testing Fundamentals

Software Testing is the process of checking software to identify defects and verify that it meets requirements.

### Objectives

- Find bugs.
- Verify functionality.
- Improve quality.
- Check performance.
- Ensure security and reliability.

### 6.1 Manual Testing

Testing performed manually by a human tester without automated test scripts.

Example: Manually entering login credentials and checking the result.

### 6.2 Automation Testing

Testing performed using tools and scripts.

Examples:

- Selenium.
- Cypress.
- Playwright.
- Jest.

### 6.3 Types of Testing

**1. Unit Testing**

Tests individual functions or components.

Example: Testing a JavaScript add() function.

**2. Integration Testing**

Checks whether multiple modules work correctly together.

Example: Checking communication between frontend and backend APIs.

**3. System Testing**

Tests the complete application as a whole.

**4. Acceptance Testing**

Checks whether software satisfies business and user requirements.

**5. Regression Testing**

Checks that new changes have not broken existing functionality.

**6. Smoke Testing**

Basic testing to verify that important application features work after a new build.

**7. Sanity Testing**

Focused testing to verify that a specific change or bug fix works correctly.

**8. Performance Testing**

Checks speed, stability and responsiveness.

**9. Security Testing**

Identifies security vulnerabilities.

### 6.4 Black Box Testing

Testing software functionality without knowing its internal code.

### 6.5 White Box Testing

Testing internal code, logic, conditions and execution paths.

### 6.6 Grey Box Testing

Testing with partial knowledge of internal implementation.

### Testing Comparison

| Testing     | Purpose                         |
| ----------- | ------------------------------- |
| Unit        | Individual component            |
| Integration | Interaction between modules     |
| System      | Complete application            |
| Acceptance  | User/business requirements      |
| Regression  | Existing features after changes |
| Smoke       | Basic build stability           |
| Sanity      | Specific change verification    |

---

## 7. Verification vs Validation

### Verification

Checks whether software is being developed correctly according to specifications.

Question: Are we building the product right?

Examples:

- Requirement reviews.
- Design reviews.
- Code inspections.

### Validation

Checks whether the developed software meets actual user needs.

Question: Are we building the right product?

Examples:

- User acceptance testing.
- Real-world application testing.

| Verification              | Validation                         |
| ------------------------- | ---------------------------------- |
| Process-oriented          | Product-oriented                   |
| Checks specifications     | Checks user requirements           |
| Reviews and inspections   | Actual testing                     |
| Are we building it right? | Are we building the right product? |

---

## 8. Software Debugging

Debugging is the process of finding, analyzing and fixing errors in software.

### Debugging Steps

1. Identify the problem.
2. Reproduce the error.
3. Find the root cause.
4. Fix the code.
5. Test the solution.
6. Verify that no new bugs were introduced.

### Types of Errors

1. Syntax Error – Incorrect programming syntax.
2. Runtime Error – Error occurring during program execution.
3. Logical Error – Program executes but produces incorrect output.

Example:

```javascript
// Syntax Error
console.log("Hello"

// Runtime Error
console.log(user.name);

// Logical Error
let total = 10 - 5; // Expected addition
```

---

## 9. Version Control System (VCS)

Version Control System tracks changes made to source code over time.

### Types

1. Local VCS – Tracks changes on a local computer.
2. Centralized VCS – Uses a central server.
3. Distributed VCS – Every developer can have a complete repository copy.

### Git

Git is a distributed version control system.

Important Git Commands:

```bash
git init
git clone <repository-url>
git status
git add .
git commit -m "Initial commit"
git push origin main
git pull origin main
git branch
git checkout main
git merge branch-name
```

### Git vs GitHub

| Git                  | GitHub                       |
| -------------------- | ---------------------------- |
| Version control tool | Cloud-based hosting platform |
| Works locally        | Hosts remote repositories    |
| Tracks code changes  | Enables collaboration        |
| Command-line tool    | Web platform and services    |

Other Git hosting platforms:

- GitLab.
- Bitbucket.

---

## 10. Agile Methodology

Agile is an approach that emphasizes flexibility, collaboration, continuous feedback and incremental delivery.

### Agile Principles

- Customer satisfaction.
- Frequent software delivery.
- Welcome changing requirements.
- Continuous collaboration.
- Working software.
- Continuous improvement.

### Scrum

Scrum is an Agile framework used to manage complex software development projects.

### Scrum Roles

**1. Product Owner**

- Manages product requirements.
- Maintains Product Backlog.
- Prioritizes features.

**2. Scrum Master**

- Helps the team follow Scrum.
- Removes impediments.
- Facilitates Scrum events.

**3. Developers**

- Build and deliver the product increment.

### Scrum Events

1. Sprint – Fixed-length development period.
2. Sprint Planning – Decide sprint goals and work.
3. Daily Scrum – Short daily coordination meeting.
4. Sprint Review – Inspect completed work with stakeholders.
5. Sprint Retrospective – Identify improvements for the next sprint.

### Scrum Artifacts

1. Product Backlog – Ordered list of product work.
2. Sprint Backlog – Selected work for the sprint.
3. Increment – Usable result of completed work.

### Important Agile Terms

**Sprint:** A fixed-length period in which a team works toward a goal.

**User Story:** A short description of a feature from the user's perspective.

Format:

As a [user], I want [feature], so that [benefit].

Example:

As a user, I want to reset my password so that I can recover my account.

**Product Backlog:** Complete prioritized list of desired product work.

**Sprint Backlog:** Work selected for the current sprint.

**Kanban:** A visual method of managing work using columns such as To Do, In Progress and Done.

---

## 11. Software Maintenance

Software Maintenance means modifying software after deployment to fix issues or improve functionality.

### Types of Maintenance

**1. Corrective Maintenance**

Fixing existing bugs.

**2. Adaptive Maintenance**

Updating software according to environmental changes.

Example: Updating software to support a new operating system.

**3. Perfective Maintenance**

Improving performance or adding features.

**4. Preventive Maintenance**

Making changes to reduce future problems.

Example: Refactoring old code.

---

## 12. Software Quality Assurance (SQA)

SQA is a systematic process used to ensure that software development processes and products meet defined quality standards.

### QA vs QC

**Quality Assurance (QA):**

- Process-oriented.
- Prevents defects.
- Focuses on development processes.

**Quality Control (QC):**

- Product-oriented.
- Identifies defects.
- Focuses on checking the actual product.

### QA vs Testing

QA focuses on improving the process to prevent defects, while testing focuses on finding defects in the software.

---

## 13. Software Metrics

Software Metrics are measurements used to evaluate software quality, productivity and performance.

Important Metrics:

1. Code Complexity – Measures code complexity.
2. Code Coverage – Percentage of code executed by tests.
3. Defect Density – Number of defects relative to software size.
4. Test Pass Rate – Percentage of tests that pass.
5. Development Time – Time required to complete development.
6. Mean Time to Recovery (MTTR) – Average time taken to restore a system after failure.
7. Mean Time Between Failures (MTBF) – Average operating time between failures.

---

## 14. Software Documentation

Documentation explains how software works, how it is developed and how it should be used.

### Types

**1. Technical Documentation**

- Architecture documents.
- API documentation.
- Database documentation.
- Code documentation.

**2. User Documentation**

- User manuals.
- Installation guides.
- FAQs.

**3. Project Documentation**

- Project plans.
- SRS.
- Design documents.
- Test reports.

**4. API Documentation**

Explains available API endpoints, request parameters, responses and authentication.

Example: Swagger / OpenAPI.

---

## 15. Software Deployment

Deployment is the process of releasing software into an environment where users can access it.

### Environments

1. Development – Developers write and test code.
2. Testing – Software is tested.
3. Staging – Production-like environment for final verification.
4. Production – Live environment used by real users.

### CI/CD

**Continuous Integration (CI):**

Developers frequently merge code changes into a shared repository, where automated builds and tests can run.

**Continuous Delivery (CD):**

Ensures software changes are prepared for release, generally with a manual production-release decision.

**Continuous Deployment:**

Automatically releases qualifying changes to production after required checks pass.

### CI/CD Tools

- GitHub Actions.
- Jenkins.
- GitLab CI/CD.
- CircleCI.

---

## 16. DevOps Fundamentals

DevOps combines Development (Dev) and Operations (Ops) practices to improve collaboration and software delivery.

### Main Objectives

- Faster software delivery.
- Automation.
- Continuous integration.
- Continuous deployment.
- Better collaboration.
- Continuous monitoring.

### Important DevOps Tools

| Category                  | Tools                    |
| ------------------------- | ------------------------ |
| Version Control           | Git                      |
| CI/CD                     | Jenkins, GitHub Actions  |
| Containers                | Docker                   |
| Container Orchestration   | Kubernetes               |
| Infrastructure Automation | Terraform                |
| Monitoring                | Prometheus, Grafana      |
| Cloud                     | AWS, Azure, Google Cloud |

---

## 17. Software Architecture Basics

Software Architecture describes the high-level structure of a software system and how its components interact.

### Common Architecture Types

**1. Monolithic Architecture**

Entire application is developed and deployed as a single unit.

Advantages:

- Simple initial development.
- Easier deployment for small applications.

Disadvantages:

- Scaling individual modules is difficult.
- Large codebase can become difficult to maintain.

**2. Microservices Architecture**

Application is divided into small independent services.

Advantages:

- Independent deployment.
- Independent scaling.
- Better service isolation.

Disadvantages:

- More operational complexity.
- Network communication challenges.
- Distributed system management.

**3. Client-Server Architecture**

Client sends requests and server processes them.

Example: Browser communicating with a backend API.

**4. Layered Architecture**

Application is divided into logical layers.

Example:

- Presentation Layer.
- Business Logic Layer.
- Data Access Layer.
- Database Layer.

### Monolithic vs Microservices

| Monolithic                     | Microservices                 |
| ------------------------------ | ----------------------------- |
| Single application unit        | Multiple independent services |
| Usually simpler initially      | More complex infrastructure   |
| Shared deployment              | Independent deployments       |
| Scaling often application-wide | Services can scale separately |

---

## 18. Software Risks

Software Risk is a possible future event that can negatively affect a project.

### Types of Risks

1. Technical Risk – Technology or implementation failure.
2. Project Risk – Budget or deadline problems.
3. Business Risk – Market or business changes.
4. Security Risk – Data breaches or vulnerabilities.
5. Operational Risk – Infrastructure or operational failures.

### Risk Management Process

1. Risk Identification.
2. Risk Analysis.
3. Risk Prioritization.
4. Risk Mitigation.
5. Risk Monitoring.

---

## 19. Important Software Engineering Principles

### DRY – Don't Repeat Yourself

Avoid duplicating the same logic unnecessarily.

### KISS – Keep It Simple, Stupid

Keep code and design simple.

### YAGNI – You Aren't Gonna Need It

Do not implement features until they are actually needed.

### SOLID Principles

Five important object-oriented design principles:

1. S – Single Responsibility Principle.
2. O – Open/Closed Principle.
3. L – Liskov Substitution Principle.
4. I – Interface Segregation Principle.
5. D – Dependency Inversion Principle.

### Refactoring

Improving the internal structure of code without changing its external behavior.

### Code Review

A process in which developers examine each other's code to identify problems and improve quality.

---

## 20. Important Software Engineering Terminology

| Term | Meaning                            |
| ---- | ---------------------------------- |
| SDLC | Software Development Life Cycle    |
| SRS  | Software Requirement Specification |
| UML  | Unified Modeling Language          |
| API  | Application Programming Interface  |
| UI   | User Interface                     |
| UX   | User Experience                    |
| QA   | Quality Assurance                  |
| QC   | Quality Control                    |
| VCS  | Version Control System             |
| CI   | Continuous Integration             |
| CD   | Continuous Delivery / Deployment   |
| TDD  | Test-Driven Development            |
| BDD  | Behavior-Driven Development        |
| MVP  | Minimum Viable Product             |
| POC  | Proof of Concept                   |
| UAT  | User Acceptance Testing            |
| RCA  | Root Cause Analysis                |
| SLA  | Service Level Agreement            |
| IDE  | Integrated Development Environment |
| WBS  | Work Breakdown Structure           |

---

# 21. Most Important Interview Questions

### Basic Questions

**Q1. What is Software Engineering?**

Software Engineering is a systematic approach to developing, testing, deploying and maintaining reliable software applications.

**Q2. What is SDLC?**

SDLC is a structured process that defines all stages of software development, from planning to maintenance.

**Q3. What are the phases of SDLC?**

Planning, Requirement Analysis, Design, Development, Testing, Deployment and Maintenance.

**Q4. What is the difference between Waterfall and Agile?**

Waterfall follows a sequential development approach, whereas Agile follows an iterative approach with continuous feedback.

**Q5. What is SRS?**

SRS is a document containing functional and non-functional requirements of a software system.

**Q6. What is a prototype?**

A prototype is an early working model used to understand and validate software requirements.

### Testing Questions

**Q7. What is software testing?**

Software testing is the process of evaluating software to identify defects and verify that it meets requirements.

**Q8. What is the difference between Unit and Integration Testing?**

Unit Testing checks individual components, while Integration Testing checks communication between multiple components.

**Q9. What is Regression Testing?**

Regression Testing ensures that new code changes have not affected existing functionality.

**Q10. What is Smoke Testing?**

Smoke Testing checks whether the basic functionalities of a new build are working.

**Q11. What is Black Box Testing?**

Testing software functionality without examining its internal code.

**Q12. What is White Box Testing?**

Testing internal code, logic and execution paths.

### Agile Questions

**Q13. What is Agile?**

Agile is an iterative software development approach that focuses on flexibility, collaboration and continuous delivery.

**Q14. What is Scrum?**

Scrum is an Agile framework used to manage complex software development projects.

**Q15. What is a Sprint?**

A Sprint is a fixed-length period during which a Scrum team works toward a specific goal.

**Q16. What is a Product Backlog?**

A prioritized list of features, improvements and other work required for a product.

### Design and Architecture Questions

**Q17. What is HLD?**

HLD describes the overall architecture and major components of a software system.

**Q18. What is LLD?**

LLD describes detailed implementation of individual modules, classes and methods.

**Q19. What is Coupling?**

Coupling describes the dependency between different software modules.

**Q20. What is Cohesion?**

Cohesion measures how closely related the responsibilities of a module are.

**Q21. What is Microservices Architecture?**

An architecture in which an application is divided into small independently deployable services.

### General Questions

**Q22. What is Debugging?**

Debugging is the process of identifying and fixing errors in software.

**Q23. What is Version Control?**

Version Control tracks and manages changes to source code over time.

**Q24. What is Git?**

Git is a distributed version control system used to track source code changes.

**Q25. What is DevOps?**

DevOps combines development and operations practices to improve software delivery and collaboration.

**Q26. What is CI/CD?**

CI/CD automates software integration, testing and delivery or deployment processes.

**Q27. What is Refactoring?**

Refactoring improves internal code structure without changing its external behavior.

**Q28. What is Software Maintenance?**

Software Maintenance involves updating, fixing and improving software after deployment.

**Q29. What is Technical Debt?**

Technical Debt refers to future maintenance costs caused by choosing an easier or quicker solution instead of a better long-term approach.

**Q30. What is TDD?**

Test-Driven Development is an approach in which tests are written before implementing the actual functionality.

---

# 22. Quick Revision

- Software Engineering = Systematic software development.
- SDLC = Complete software development life cycle.
- Waterfall = Sequential model.
- Agile = Iterative model.
- Spiral = Risk-based model.
- Prototype = Early working model.
- SRS = Requirement specification document.
- Functional Requirements = What system does.
- Non-Functional Requirements = How well system works.
- HLD = Overall architecture.
- LLD = Detailed design.
- High Cohesion = Good.
- Low Coupling = Good.
- Unit Testing = Individual components.
- Integration Testing = Combined components.
- System Testing = Complete system.
- Acceptance Testing = User requirements.
- Regression Testing = Existing functionality after changes.
- Verification = Are we building the product right?
- Validation = Are we building the right product?
- Git = Version Control System.
- Agile = Flexible development.
- Scrum = Agile framework.
- Sprint = Fixed-length development period.
- QA = Defect prevention through process quality.
- QC = Product quality checking.
- CI = Continuous Integration.
- CD = Continuous Delivery / Deployment.
- DevOps = Development + Operations.
- DRY = Don't Repeat Yourself.
- KISS = Keep It Simple.
- YAGNI = You Aren't Gonna Need It.
- SOLID = Five object-oriented design principles.

---

# 23. Self-Assessment Practice

1. Explain all seven SDLC phases.
2. Differentiate between Waterfall and Agile.
3. Explain functional and non-functional requirements.
4. What is SRS and why is it important?
5. Explain HLD and LLD with examples.
6. What is the difference between Coupling and Cohesion?
7. Explain all major software testing types.
8. Differentiate between Verification and Validation.
9. Explain Scrum roles and events.
10. What is the difference between Git and GitHub?
11. Explain CI/CD with an example.
12. Differentiate between Monolithic and Microservices Architecture.
13. Explain the four types of software maintenance.
14. What are DRY, KISS and YAGNI?
15. Explain all five SOLID principles.

**End of Software Engineering Fundamentals Notes.**
