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


## Advantages Of Api Testing

* *Immediate Testingof Business Logics :* There is no need to wait untill whole application is ready- you can start writing API test at very early stage in sprintcycle.

* *Less Brittle and easier to maintain that other tests :* Traditional UI's are difficult to maintain and UI constantly keeps on changing and hence need to change test script frequently and also need to write long codes.

* *Faster Test Execution :*  UI is slow very slow as compared to Api

* *Faster Root cause Analysis :* As in UI execution takes long time and hence failure cause analysis also takes time. 