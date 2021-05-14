# Layers of Automation framework

The basic automation framework is divided into the following 3 Layers: 

* *Test Layer*
* *Business Layer*
* *Core Layer*

# Test Layer: 

* This layer as from the name is suggested is the one which basically contains various test cases and test scenarios, test data etc.
* In such architecture, test layer typically contains test scenarios. They may be written in programming language or DSL (like Gherkin in BDD inspired solutions). The key requirement for this layer would be:
 * Test scenarios communicates test intention, not implementation
 * Test scenarios structured in a way it doesn't takes ages to find a test for specific feature

This layer can be further splitted into:

* System/Functional Test Layer
* Integration Test Layer
* Unit test layer

The above sequence also constitutes test pyramid where Unit test is at bottom and System test is at top.

The main reason for maintaining test pyramid is:

* Lead to an increase in overall code quality and design
* Catch bugs before production releases (or classify any sneaky ones that make it to production)
* Serve as documentation from the project
* Increase trust in the development team to release the highest quality product possible.

## Layers of Test Pyramid
The Testing Pyramid has three classic layers:

* **Unit tests are at the bottom.** Unit tests directly interact with product code, meaning they are “white box.” Typically, they exercise functions, methods, and classes. Unit tests should be short, sweet, and focused on one thing/variation. They should not have any external dependencies – mocks/monkey-patching should be used instead.
* **Integration tests are in the middle.** Integration tests cover the point where two different things meet. They should be “black box” in that they interact with live instances of the product under test, not code. Service call tests (REST, SOAP, etc.) are examples of integration tests.
* **End-to-end tests are at the top.** End-to-end tests cover a path through a system. They could arguably be defined as a multi-step integration test, and they should also be “black box.” Typically, they interact with the product like a real user. Web UI tests are examples of integration tests because they need the full stack beneath them.
All layers are functional tests because they verify that the product works correctly.

## Why Test Pyramid is in triangular form

The Testing Pyramid is triangular for a reason: **there should be more tests at the bottom and fewer tests at the top.** Why?

1. **Distance from code.** Ideally, tests should catch bugs as close to the root cause as possible. Unit tests are the first line of defense. Simple issues like formatting errors, calculation blunders, and null pointers are easy to identify with unit tests but much harder to identify with integration and end-to-end tests.
2. **Execution time**Unit tests are very quick, but end-to-end tests are very slow. Consider the Rule of 1’s for Web apps: a unit test takes ~1 millisecond, a service test takes ~1 second, and a Web UI test takes ~1 minute. If test suites have hundreds to thousands of tests at the upper layers of the Testing Pyramid, then they could take hours to run. An hours-long turnaround time is unacceptable for continuous integration.
3. **Development cost.** Tests near the top of the Testing Pyramid are more challenging to write than ones near the bottom because they cover more stuff. They’re longer. They need more tools and packages (like Selenium WebDriver). They have more dependencies.
4. **Reliability.** Black box tests are susceptible to race conditions and environmental failures, making them inherently more fragile. Recovery mechanisms take extra engineering.

The total cost of ownership increases when climbing the Testing Pyramid. When deciding the level at which to automate a test (and if to automate it at all), taking a risk-based strategy to push tests down the Pyramid is better than writing all tests at the top. Each proportionate layer mitigates risk at its optimal return-on-investment.

# Business Layer:

This is the layer where business logic is written where we perform logical checks and assertions and validations. This is the heart of the framework. In case of cucumber step definition files comes under this layer. **Various Actions and Assertions are performed in this layer.**

# Core Layer: 

This is the layer where we keep all the set up related thing like if we are creating a page object model with cucumber then all the pages with OR's are kept in this layer and also WebDriver engines, wrappers and reportings, TestRunners, Starters, Classes to read properties.

# Type of Testings or Test Design techniques

## 1. Static Testing:

* No code is executed
* Done to catch the bugs/defects at the initial stage of development
* Code Reviews, Design document review, Requirement review, static code analysis are done under static testing.
* Static testing is about prevention of defects
* Also called as **Verification testing**

### Static testing techniques:

**Classes of Static Test Design Techniques:**


   | Manual              | With Help of Tools                            |
   | ------------------- |:--------------------------------------:       |
   |Walk through         |    Analysis of coding standard using compiler |
   | Informal review     |    Analysis of code metrics                   |
   | Technical review    |    Analysis of code structure                 |
   |Inspection           |                                               |
   | Static code review  |                                               |

**Manual Static test design techniques**

1. **Informal Reviews:** No process is followed, just randomly review the code or documnets and give the comments.
2. **Technical Reviews:** Peers with technical expertise reviews the code and technical design documents and share the inputs as per the outcome of the discussion. Test Strategy, Test Plan and requirement specification documents are majorly reviewed in this.
3. **Walkthrough:** Author of the workproduct gives the technical walkthrough of the product.
4. **Inspection:** It is a formal review done by experts. They follow strict process to find the bugs in requirements and codes. The review is done on the basis of the checklist and defects if found are reported to the concerned team.
5. **Static code review:** This process involves the source/test code review by team or individuals with technical expertise. **It checks the syntax of the code, coding standards, code optimization, etc.** This is also termed as white box testing.This review can be done at any point during development. 

**Static test design techniques with the help of tool**

1. **Analysis of coding standard using compiler:** In this code standards like naming conventions, syntax, line spacing use of white spaces, alignments etc are validated using the help of compilers like we use some pre-defined formats in Intellij and in Eclipse.

2. **Analysis of code metrics:** It keeps a check on cyclomatic numbers, dept of nesting and number of lines of codes. This information helps to keep a check on the code and prevents it from becoming excessively lengthy, unwieldy, difficult to understand and maintain.

3. **Analysis of Code Structure:**
An analysis of the code structure gives an idea about the effort required to write or understand the code and to test it using particular tools and techniques

## 2. Dynamic Testing

* Done after source code is completed and is in working state
* In this code is executed and then functionality is validated and hence also called as Validation testing.
* As we execute the code and hence it is about finding the defects and not preventing them like in static testing.
* Dynamic testing is performed at all levels of testing and it can be either black or white box testing.

### Dynamic testing techniques:

1. **Unit Testing**
2. **Integration Testing**
3. **System testing**

Dynamic test design techniques can be further classified into:
* Specification-based (black-box, also known as behavioral techniques)
* Structure-based (white-box or structural techniques
* Experience- based

   | Specification-based(Black Box) | Structure-based(White box)  |Experience-Based|
   | ------------------------- |:--------------------------------------: |--------------|
   | Boundary Value Analysis   | Statement or Line coverage              |Exploratory Testing|
   | Equivalance Partitioning  | Condition or predicate coverage         | Fault attack|
   | Decision Table testing    | Decision or branch coverage             ||
   | State transition diagram  | Multiple condition coverage             ||
   | Use Case Testing          |                                         ||

**Important Points to Keep in Mind while Designing Test Cases**

1. **The only way to attain 100% logical coverage is to use the decision test design techniques** --Important Point
2. Boundary value analysis and equivalence partitioning are the best methods to cover the range of array inputs
3. Permutations and combinations can be used for field level validations

# KEY DIFFERENCE BETWEEN STATIC AND DYNAMIC TESTING AND DESIGN TECHNIQUES
* Static testing was done without executing the program whereas Dynamic testing is done by executing the program.
* Static testing checks the code, requirement documents, and design documents to find errors whereas Dynamic testing checks the functional behavior of software system, memory/CPU usage and overall performance of the system.
* Static testing is about the prevention of defects whereas Dynamic testing is about finding and fixing the defects.
* Static testing does the verification process while Dynamic testing does the validation process.
* Static testing is performed before compilation whereas Dynamic testing is performed after compilation.

**References:**

- [Guru99](https://www.guru99.com/static-dynamic-testing.html#:~:text=Static%20testing%20is%20about%20the,testing%20is%20performed%20after%20compilation.)
- [Test Design Techniques](https://www.invensis.net/blog/software-test-design-techniques-static-and-dynamic-testing/)


## Advantages Of Api Testing

* *Immediate Testingof Business Logics :* There is no need to wait untill whole application is ready- you can start writing API test at very early stage in sprintcycle.

* *Less Brittle and easier to maintain that other tests :* Traditional UI's are difficult to maintain and UI constantly keeps on changing and hence need to change test script frequently and also need to write long codes.

* *Faster Test Execution :*  UI is slow very slow as compared to Api

* *Faster Root cause Analysis :* As in UI execution takes long time and hence failure cause analysis also takes time. 