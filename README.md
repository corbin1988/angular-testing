# Angular Testing

## Table of Contents



- [Introduction](#introduction)
  - [Bug Detection and Prevention](#bug-detection-and-prevention)
  - [Enhances Software Quality](#enhances-software-quality)
  - [Improved Code Quality](#improved-code-quality)
  - [Increased Confidence in Code Changes](#increased-confidence-in-code-changes)
  - [Supports Continuous Integration and Deployment](#supports-continuous-integration-and-deployment)
  - [Documentation and Understanding](#documentation-and-understanding)

- [Testing Philosophy](#testing-philosophy)
  - [Code Coverage](#code-coverage)
  - [Software Opinionation](#software-opinionation)
    - [Opinionated Software](#opinionated-software)
      - [Pros](#pros)
      - [Cons](#cons)
    - [Unopinionated Software](#unopinionated-software)
      - [Pros](#pros-1)
      - [Cons](#cons-1)
  - [How much to test?](#how-much-to-test)
    - [No Coverage/No Tests](#no-coverageno-tests)
    - [High code coverage](#high-code-coverage)
    - [Some Code Coverage](#some-code-coverage)

- [Testing Methodology/Workflow](#testing-methodologyworkflow)
  - [Writing Tests Before Code Implementation With TDD](#writing-tests-before-code-implementation-with-tdd)
  - [Writing Tests While Implementing Code With BDD](#writing-tests-while-implementing-code-with-bdd)
  - [Writing Tests After Code Has Been Written With Post-Development Testing or Post-Implementation Testing](#writing-tests-after-code-has-been-written-with-post-development-testing-or-post-implementation-testing)

- [Types of Tests](#types-of-tests)

## Introduction

Software testing is the process of assessing the functionality of a software program. The process checks for errors and gaps and whether the outcome of the application matches desired expectations before the software is installed and goes live. The main things software testing hopes to accomplish are:

### Bug Detection and Prevention:
Testing helps identify and eliminate bugs and errors in the early stages of development. This prevents issues from escalating into critical problems during production, saving time and resources.
### Enhances Software Quality:
Thorough testing ensures that software meets the specified requirements and adheres to quality standards. This, in turn, leads to the delivery of a high-quality product that satisfies user expectations.
### Improved Code Quality:
Writing testable code encourages developers to follow best practices, resulting in cleaner, modular, and maintainable code. This contributes to better overall code quality and reduces technical debt.
### Increased Confidence in Code Changes:
Continuous testing provides developers with confidence when making changes or adding new features. Knowing that existing functionality is safeguarded by tests allows for more agile development and iteration.
### Supports Continuous Integration and Deployment:
Testing is a cornerstone of continuous integration and continuous deployment (CI/CD) pipelines. Automated tests ensure that code changes do not introduce regressions, enabling a smoother and faster release process.
### Documentation and Understanding:
Tests serve as a form of documentation, providing insights into the expected behavior of the code. This aids not only in understanding existing code but also in onboarding new team members.

## Testing Philosophy

One of the reasons software testing is so difficult is because the multitude of approaches. Different companies, programming languages, frameworks, and individuals hold varying opinions on how software should be tested. In this section we’ll speak about three things: code coverage, opinionation, why companies have different levels of testing, and testing methodology/workflow. 

### Code Coverage

Code coverage in essence is how much of the code base is tested. 

### Software Opinionation

Software opinionation refers to a design or architectural approach that includes strong, often predefined, opinions about how the software should be structured, organized, and implemented. Opinionated software typically enforces a specific set of conventions, best practices, or design patterns, guiding developers in making certain decisions.

Conversely, unopinionated or flexible software allows developers more freedom and choices in how they structure and implement their code. It provides a framework or toolset without imposing strict rules or preferences.

#### Opinionated Software

##### Pros:
Clear guidelines and conventions lead to consistent code.
Faster development due to reduced decision-making.
Can be beneficial for teams where consistency is crucial.
##### Cons:
Less flexibility for developers who prefer alternative approaches.
May not fit well with specific project requirements or constraints.

#### Unopinionated Software:

##### Pros:
Offers flexibility, allowing developers to choose their preferred structures.
Adaptable to diverse project requirements.
Appeals to developers who value creative freedom.
##### Cons:
May lead to inconsistencies in code style and structure.
Increased decision-making can slow down development for some teams.
An example of opinionation in software development is the choice of a web framework. Some frameworks, like Ruby on Rails, are opinionated and come with a set of conventions and best practices that developers are encouraged to follow. On the other hand, frameworks like Express.js for Node.js are unopinionated, providing more flexibility and leaving many decisions to the developers.

Ultimately, whether a software project is opinionated or unopinionated depends on the specific goals, preferences, and requirements of the developers and the project itself.

### How much to test?

You will get software testing evangalists on one side saying "always!" and on the other side saying "never!" When it comes to testing coverage you'll also get evaganlists that preach "you should aim as close to 100% code coverage as you can!" So what's the truth? The answer, as always in software development, is it depends. 

It's fair to say that the more test coverage the more opinionated a codebase becomes. As stated above, there's reasons you might want more opinionation and more flexability. The same thing can be said about adding in tests. For ease we'll discuss three code coverage scenarios: No testing/No code coverage, some code coverage, high code coverage:

#### No Coverage/No Tests

Since writing tests comes with opinions and time overhead, many companies, especially smaller ones like startups, choose not to write frontend tests. The primary reason is a need for flexibility and code velocity. For startups, the goal is to roll out features as quickly as possible to users. Writing tests can not only consume time but may also impede product development in a highly competitive market. Additionally, writing tests requires more developer time, translating to increased costs for the company. This trade-off between speed and testing is a common consideration in resource-constrained environments.

Another philosphy that preaches not implenting tests is "build nets, not guard rails." The idea is that code should follow a certain standard where it's acceptable to fail. Instead of using opinionation that can make a codebase rigid and hard to iterate with, you should use specific standards that tries to prevent bugs that unit tests could catch. For example, Typescript making sure a functions inputs and outputs are valid. 

The last argument against testing on the frontend is the nature of the javascript ech system itself. While most frameworks and libraries seem to be going towards longterm stability and support, it wasn't always like that. The life cycle of a javascript app for many smaller companies might be that they're writing the app to be rewritten later on. In this case, the overhead of writing tests might not be worth it.

#### High code coverage

In the [introduction](#introduction) we provided examples as to why you should test. A good rule of thumb for why companies, teams, or individuals would choose to implement high test coverage are when the stakes for product failure are high to the user. For example the following applications:

- Anything based around safety that could mean life or death:
  - Medical devices
  - Safety Equipment
- Financial transactions
- Anything that poses a major security risk (personal data, secrets, sensitive data in general)
- Devices or software that is only purchased once, isn't frequently updated, and needs to run reliably:
  - Hardware devices that don't connect to the internet
  - Games that aren't connected to the internet

Anything where the margin for error needs to be low and the consequences of a bug in the code could cause something catastrophic to happen should have high test coverage.

#### Some Code Coverage

Maintaining a test coverage range of 40% to 70% offers a balanced approach that combines flexibility with the assurance of testing. Striking this middle ground accommodates scenarios where the need for adaptability in building new features coexists with the necessity of rigorous testing, particularly in critical areas like security and databases.

In software development, the requirement for untested flexibility arises when innovating and introducing new features. This level of code coverage acknowledges that not every aspect of the codebase demands immediate testing. Instead, it reserves the freedom to explore creative solutions and iterate rapidly, essential in environments where agility is paramount.

Simultaneously, the prescribed coverage range ensures a baseline of testing, especially in realms crucial to the system's integrity. Security considerations and interactions with databases, where data accuracy and reliability are paramount, benefit from a more comprehensive testing approach. Striking a balance in code coverage acknowledges the dual needs of development—innovation and reliability—creating a pragmatic framework for effective software testing.

### Testing Methodology/Workflow

Testing workflows and methodologies dictate when tests are written during the development process. For simplicity, we'll categorize this into three sections: testing before code implementation (TDD), testing while writing code (BDD), and testing after code has been written (PDT).

#### Writing Tests Before Code Implementation With TDD

Test-Driven Development (TDD) falls into this category, where tests are written before the actual code implementation. The idea is to define the expected behavior first and then write code to fulfill those expectations.

#### Writing Tests While Implementing Code With BDD

Behavior-Driven Development (BDD) is a testing methodology where tests are written concurrently with code development. In BDD, the focus is on describing the expected behavior of the software using natural language specifications, often expressed in "Given-When-Then" syntax. This approach encourages collaboration between developers, QA, and non-technical stakeholders, fostering a shared understanding of the software's functionality. BDD aligns testing with the ongoing development process, allowing for continuous validation of expected behaviors as the code evolves.

#### Writing Tests After Code Has Been Written With Post-Development Testing or Post-Implementation Testing

Post-Development Testing or Post-Implementation Testing is when tests are created after the code has been implemented. This is more common in traditional development processes or when testing is a separate phase following code implementation.

**Disclaimer** 

The amount of software testing that can be introduced into codebase can also be based on person prefrence of a developer or team with no rhyme or reason to their decisions other than they like testing or hate it. 

## Types of Tests

Testing in Angular applications involves various types of tests that serve different purposes in ensuring the reliability and functionality of the software. These tests can be broadly categorized into three main types: Unit Testing, Integration Testing, and End-to-End (E2E) Testing.

### Unit Testing:

#### Purpose

Focuses on testing individual units or components of the application in isolation.

#### Scope 

Tests the smallest parts of the code, such as functions or methods, to ensure they work as expected.

#### Advantages 

Helps identify and fix bugs at an early stage, promotes modular and maintainable code.

### Integration Testing:

#### Purpose: 

Verifies that different units or components work together as expected when integrated.

#### Scope: 

Tests interactions between multiple units to ensure the seamless collaboration of integrated parts.

#### Advantages: 

Detects issues arising from the combination of units, ensuring the overall system functions correctly.

#### End-to-End (E2E) Testing:

#### Purpose: 

Evaluates the entire application workflow, simulating real user scenarios.

#### Scope: 

Tests the application as a whole, including its user interface, to ensure all components work together in a real-world setting.

#### Advantages: 

Provides a comprehensive view of the application's behavior, helping catch issues related to the entire user journey.
