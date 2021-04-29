# Sharing of Data in different steps in cucumber feature file.

A scenario in Gherkin is created by steps. Each step depends on previous steps. This means that we must be able to share state between steps.

You can write all the steps of a feature file in single step definition but there could be an instance where you want to use any pre-defined step in one step definition class into other step definition class. There could be two ways to do that. 

**a)** Either write the whole implementation in other step definition class which is redundant and a bad approach too.

**b)** Using Context class.

Now Context class can also have two different categories:

- ScenarioContext : Used when you want to use the data sent in one testStep in other test step within same scenario.
```
  Given User slelects the dress
  When user goest to the order details page
  Then User validates the order
```
Now you can see that the data sent in Given is validated in Then.

- TestContext
 

## 1. Scenario Context:

**Scenario Context** is a class that holds the test data information specifically. It actually uses the Test Context to travel the information between various steps. Within this ScenarioContext class, you can create any number of fields to store any form of data. It stores the information in the key-value pair and again, value can be of any type. It can store String, Boolean, Integer or maybe a Class. Also, the important point here is that the information which we store in the Scenario Context is generated run time. Means during the run if you wish to store some information, you will use Scenario Context.

## 2. Test Context: This is the way to split the steps into multiple classes. This is basically used to share the state between steps in cucumber

Divide steps between different classes according to something that is logical for the team. All steps regarding goods goes into one step class and all steps regarding customers in another. Other axes are possible and perhaps better. If you make a mistake and realize it, move the methods to a better home. Moving the steps around is not a humongous task.

*The next problem you will have to solve is to handle a shared state between the steps. When there was only one class, an instance variable or two was probably enough. Now you need to solve the problem with a shared state between the two, or more, classes with steps.*

Answer to the above problem is **Dependency Injection**

**Dependency injection (DI) is the concept in which objects get other required objects from outside. DI can be implemented in any programming language. The general concept behind dependency injection is called Inversion of Control. A Java class has a dependency on another class, if it uses an instance of this class.**

## Dependency injection
How do you share state between different classes?

In Cucumber for Ruby, there is a world object where the shared state lives. It is re-created for each scenario. Each scenario has a fresh world and leakage between scenarios through the world object is unlikely.

**A naive solution in Java** could be to share a state using a **class with static fields**. This would work. It is unfortunately very easy for information to leak from one scenario to another. Static fields are not cleared while the JVM is running. To clear them, you would either have to reset them manually or restart the JVM. Both ways are cumbersome.

How do you share state in Java then? The idiomatic solution in Java is to use dependency injection. That is, inject a common object(Object of Test Context class in each step def class) in each class with steps. An object that is recreated every time a new scenario is executed.

**Dependency injection can be done in many ways. A simple solution is to to inject dependencies through the constructor. This is sometimes referred to as __Constructor Dependency Injection, CDI.__**

Cucumber-JVM support many different dependency injection frameworks. One of the least intrusive frameworks is called **PicoContainer.** It is a minimalistic framework that is invisible everywhere except in the build script where a dependency to it has to be declared.

## A small example in two parts

Lets look at a small example and see how it can be implemented with one step definition class and then extend it so the steps are implemented in two different classes with a common object to share state.

The narrative for the example goes like this:

Joanna bought an electric kettle for $100. Unfortunately, it broke after a week
Joanna brings the kettle back to the store and asks for a refund
She has the receipt so there is no problem getting the refund
The store manager Joe refunds her the same value as she payed for the kettle
This example can be documented using Gherkin like this this:

*src/test/resources/se/thinkcode/refund-faulty-items.feature*

```
Feature: Refund faulty items

  Broken items should be refunded if you have receipt 

  Scenario: Returning a broken kettle to the store
    Given that Joanna bought a faulty kettle for $100
    When she return the kettle to the store
    And she show her receipt
    Then she will get $100 refunded
```

**Steps that support this scenario may be implemented as:**

*src/test/java/se/thinkcode/steps/RefundItems.java*

```
package se.thinkcode.steps;

import cucumber.api.java.en.Given;
import cucumber.api.java.en.Then;
import cucumber.api.java.en.When;
import se.thinkcode.Customer;
import se.thinkcode.Item;

import static org.hamcrest.CoreMatchers.is;
import static org.hamcrest.MatcherAssert.assertThat;

public class RefundItems {
    private Customer customer;
    private Item item;

    @Given("^that (.*) bought a faulty (.*) for \\$(\\d+)$")
    public void that_bought_a_faulty_kettle(String name, String itemType, int price) throws Throwable {
        customer = new Customer(name);
        item = new Item(itemType, price);
    }

    @When("^she return the (.*) to the store$")
    public void return_the_an_item_to_the_store(String itemType) throws Throwable {
        Item returnedItem = new Item(itemType);
        assertThat(item, is(returnedItem));
    }

    @When("^she show her receipt$")
    public void she_can_show_a_receipt() throws Throwable {
        customer.refund(item.getPrice());
    }

    @Then("^she will get \\$(\\d+) refunded$")
    public void she_will_get_$_back(int expected) throws Throwable {
        assertThat(customer.getRefunded(), is(expected));
    }
}
```

**A Maven pom file that supports the project may look like this:**

*pom.xml*

```
<?xml version="1.0" encoding="UTF-8"?>
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>se.thinkcode.blog</groupId>
    <artifactId>example-no-shared-state</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-java</artifactId>
            <version>1.2.5</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-junit</artifactId>
            <version>1.2.5</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```
It declares two dependencies to Cucumber. This is enough to get this example working.

A runner class that will connect the specification in Gherkin with the steps implemented in Java looks like this:

*src/test/java/se/thinkcode/RunCukesTest.java*

```
package se.thinkcode;

import cucumber.api.junit.Cucumber;
import org.junit.runner.RunWith;

@RunWith(Cucumber.class)
public class RunCukesTest {
}
```

The runner class can be called anything but the Maven test runner searches the class path for classes that starts or ends with the word test. I prefer classes that ends with the word test. This means that naming it RunCukesTest will allow the test runner to find it and execute it as a part of the regular Maven build. It will be executed during the test phase.

This executable specification will be executed when you do

```mvn test```

## Different concepts
This example talks about two different concepts

- Items sold in the store, Kettles for example
- Money and rules for refunding

Because it is so small, you would probably not split it yet in a real world implementation.

## Splitting the steps
One thing to notice is that the feature file and the runner class should not be touched at all. They are unaffected by the separation of steps.

My first change is to add a dependency to PicoContainer, a dependency injection framework, in the Maven pom.

```
<dependency>
    <groupId>info.cukes</groupId>
    <artifactId>cucumber-picocontainer</artifactId>
    <version>1.2.5</version>
    <scope>test</scope>
</dependency>
```

**The new Maven pom now looks like this:**

*pom.xml*

```
<?xml version="1.0" encoding="UTF-8"?>
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>se.thinkcode.blog</groupId>
    <artifactId>example-shared-state</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-java</artifactId>
            <version>1.2.5</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-junit</artifactId>
            <version>1.2.5</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>info.cukes</groupId>
            <artifactId>cucumber-picocontainer</artifactId>
            <version>1.2.5</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

Next step is to create two classes for the steps. I will call them **CustomerSteps** and **GoodsSteps.** The idea is that they will share state between steps that depends on the result of an earlier step in the scenario. Sharing state can be done in different ways, I will use a common TestContext.java object. This solution is very similar to the one of a shared state with a world object in Ruby. Remember that the world object in Ruby, as well as the shared world injected by PicContainer, are recreated for every scenario. Leakage between scenarios through the TestContext.java is therefore not possible.

**The shared TestContext.java object looks like this:**

*src/test/java/se/thinkcode/steps/TestContext.java*

```
package se.thinkcode.steps;

import se.thinkcode.Customer;
import se.thinkcode.Item;

public class TestContext {
    Customer customer;
    Item item;
}
```

It only contains a reference to a Customer and a reference to an Item. I decided to make the fields package private to make it easy to refer to them. This is not necessarily the idiomatic way in Java, but it made the changes I had to do to my step implementations small.

The implementations of **GoodsSteps** and **CustomerSteps** both contains a constructor that requires an instance of the TestContext object. Since I included PicoContainer, the classes will be created and injected using this constructor with the same instance of TestContext.

*src/test/java/se/thinkcode/steps/GoodsSteps.java*

```
package se.thinkcode.steps;

import cucumber.api.java.en.Given;
import se.thinkcode.Customer;
import se.thinkcode.Item;

public class GoodsSteps {
    private TestContext testContext;

    public GoodsSteps(TestContext testContext) {
        this.testContext = testContext;
    }

    @Given("^that (.*) bought a faulty (.*) for \\$(\\d+)$")
    public void that_bought_a_faulty_kettle(String name, String itemType, int price) throws Throwable {
        testContext.customer = new Customer(name);
        testContext.item = new Item(itemType, price);
    }
}
```

The implementation of **CustomerSteps** has an identical constructor as **GoodsSteps**.

*src/test/java/se/thinkcode/steps/CustomerSteps.java*

```
package se.thinkcode.steps;

import cucumber.api.java.en.Then;
import cucumber.api.java.en.When;
import se.thinkcode.Item;

import static org.hamcrest.CoreMatchers.is;
import static org.hamcrest.MatcherAssert.assertThat;

public class CustomerSteps {
    private World world;

    public CustomerSteps(World world) {
        this.world = world;
    }

    @When("^she return the (.*) to the store$")
    public void return_the_an_item_to_the_store(String itemType) throws Throwable {
        Item returnedItem = new Item(itemType);
        assertThat(world.item, is(returnedItem));
    }

    @When("^she show her receipt$")
    public void she_can_show_a_receipt() throws Throwable {
        world.customer.refund(world.item.getPrice());
    }

    @Then("^she will get \\$(\\d+) refunded$")
    public void she_will_get_$_back(int expected) throws Throwable {
        assertThat(world.customer.getRefunded(), is(expected));
    }
}
```
Executing this will have the same result as the previous example where the state was shared using instance variables in the step definition class. The difference is that the state shared between the steps now is contained in the world object.

**Question:** Is it mandatory that we can only add references of various step definitions in TestContext.java?

**Answer :** No, testContext basically behavious as a central facilitator class to share states between differnt step def class so in this class you can have instances of different data provider or other classes also which are used by multiple step definition classes like:

If we are using multiple cards and the cards are stored in Cards.java class then we can create instance of cards class in TestContext.java class so that this card class can be easily called using the reference of testContext class.
 
**Reference : http://www.thinkcode.se/blog/2017/04/01/sharing-state-between-steps-in-cucumberjvm-using-picocontainer**

## How to write a good Feature file

> Don't write feature files Imperatively like traditional *procedure-driven* functional test where we give step by step instructions with actions and expected results

```
# BAD EXAMPLE! Do not copy.
Feature: Google Searching

  Scenario: Google Image search shows pictures
    Given the user opens a web browser
    And the user navigates to "https://www.google.com/"
    When the user enters "panda" into the search bar
    Then links related to "panda" are shown on the results page
    When the user clicks on the "Images" link at the top of the results page
    Then images related to "panda" are shown on the results page
```

**Below are a number of tidbits for good style and structure:**

> Focus a feature on customer needs.
> Limit one feature per feature file. This makes it easy to find features.
> Limit the number of scenarios per feature. Nobody wants a thousand-line feature file. A good measure is a dozen scenarios per feature.
> Limit the number of steps per scenario to less than ten.
> Limit the character length of each step. Common limits are 80-120 characters.
> Use proper spelling.
> Use proper grammar.
> Capitalize Gherkin keywords.
> Capitalize the first word in titles.
> Do not capitalize words in the step phrases unless they are proper nouns.
> Do not use punctuation (specifically periods and commas) at the end of step phrases.
> Use single spaces between words.
> Indent the content beneath every section header.
> Separate features and scenarios by two blank lines.
> Separate examples tables by 1 blank line.
> Do not separate steps within a scenario by blank lines.
> Space table delimiter pipes (“|”) evenly.
> Adopt a standard set of tag names. Avoid duplicates.
> Write all tag names in lowercase, and use hyphens (“-“) to separate words.
> Limit the length of tag names.

## Why Cucumber?
Before answering this question go through the details of the cucumber tool mentioned below:

## What is cucumber?
Cucumber is a tool for collaboration and testing. It is used to create examples of behaviour that are executable. Creating examples in a collaborative way emphasize close cooperation between business analysts, testers and developers. The examples they come up with can be used as acceptance tests for the system being developed. It can be used as a testing tool where the tests are defined in a business friendly language while still being executable.

## Goal
Our goal is to create a common understanding of the problem and therefore simplify the communication between all parties involved. We would also like to get something that is possible to use for automating the verification of the resulting program. That is, use as a base for test automation of the system.

## Why use Cucumber?
> The main reason for using Cucumber is that it is easy to express requirements using concrete examples that are hard to interpret in more than one way. It means that a customer that may describe a problem vague has to be very precise and use clear examples for describing the behaviour they actually want. These examples are easy for testers and developers to understand and discuss with the customer.

> Also, the feature files we write in cucumber is the implementation of BDD where we are illustrating business rules with examples 

> **Cucumber lets you keep specifications, automated tests and documentation in the same place - _a single source of truth that never gets out of sync._** Basically it gives us executable specifications.

Imagine the impact this would have on the development and maintenance costs of your projects. Shorter feedback cycle to fix bugs. Less rework because of misunderstood requirements.

> We are able to replace vaguely defined problems with well defined, concrete examples and get acceptance criteria that can be automated in the process.

## Why not write source code?
Being concrete and precise is the same thing as writing source code. Why don't we just write source then? Depending on the receiver, this may be a good or bad idea. However, most of our customer can't read, or write source code. This is the reason why we have a communication gap that we must bridge. It is also the reason why we developers have a job, our customers can't do the job we do.

## Executing cucumber tests in parallel

The cucumber tests can be executed in parallel using both **Junit** and **TestNg** but there is a difference in both implementations which is explained below:

## Parallel Execution using Junit

* Cucumber can be executed in parallel using Junit and Maven test execution plugins.
* In Junit the **feature files run in parallel and not the scenarios** in the feature files. Means if there are 10 feature files in a package then all of them will be executed parallely using Junit and all the scenarios in an individual feature file will run on a single thread.
* Maven surefire or failsafe plugins can be used to execute the runners. 

## Steps to follow to achieve parallel execution using JUnit

**1. Surefire Plugin**

* Create a Maven project.
* Create a package and keep feature files you want to execute in parallel in that package.
We are assuming we have kept 2 feature files.
* Add step definition
* Create runner class a basic one.

* Add the Surefire plugin configuration to the build section to the POM.

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.0</version>
    <configuration>
        <parallel>methods</parallel>
        <useUnlimitedThreads>true</useUnlimitedThreads>
    </configuration>
</plugin>
```

**In case of multiple runner files**

In case of multiple runners one can also set the **parallel option to classesAndMethods or classes in addition to methods**.
```
<configuration>
    <parallel>classesAndMethods</parallel>
    useUnlimitedThreads>true</useUnlimitedThreads>
</configuration>
```

* Use the **mvn verify** or a suitable command to execute the POM. This should run in parallel threaded mode.

**2. Using maven failsafe plugin**

To execute using a **Maven Failsafe plugin** include the below configuration in the build section to the POM. Rename the runner class to RunCucumberIT.

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-failsafe-plugin</artifactId>
    <version>2.22.0</version>
    <executions>
        <execution>
            <goals>
                <goal>integration-test</goal>
                <goal>verify</goal>
            </goals>
            <configuration>
                **<parallel>methods</parallel>**
                **<useUnlimitedThreads>true</useUnlimitedThreads>**
            </configuration>
        </execution>
    </executions>
</plugin>
```

* To set the thread count to a specific number instead of useUnlimitedThreads use the below setting.
```
<configuration>
    <parallel>methods</parallel>
    <threadCount>4</threadCount>
</configuration>
```
* The thread count in the above setting is 4 threads per core. If you want this to be 4 threads across all cores set the perCoreThreadCount to false.

```
<configuration>
    <parallel>methods</parallel>
    <threadCount>4</threadCount>
    <perCoreThreadCount>false</perCoreThreadCount>
</configuration>
```

## Steps to follow to achieve parallel execution using TestNg**

* Using TestNg you can overcome the limitation of running all the feature files together in parallel which was there in Junit.

* Cucumber can be executed in parallel using **TestNG and Maven test execution plugins by setting the dataprovider parallel option to true**.
* In **TestNG the scenarios and rows in a scenario outline are executed in multiple threads.** One can use either Maven Surefire or Failsafe plugin for executing the runners.

>> Now follow the following steps:

* Create a maven project or take any existing project
* Add a package and add feature files in that package.
* Add a cucumber runner **by extending the AbstractTestNGCucumberTests class and overriding the scenarios method in the parallel package (same name as step definition package, not neccesarily same package but name should be same) in src/test/java folder.. Set the parallel option value to true for the DataProvider annotation.**

```
package parallel;

import org.testng.annotations.DataProvider;
import io.cucumber.testng.AbstractTestNGCucumberTests;

@RunWith(Cucumber.class)
@CucumberOptions(
        format = {"pretty"},
        glue = {"parallel"},
        features = "src/test/resources/cucumber/acquirer_features/parallelTest.feature",
        strict = true,
        snippets = SnippetType.CAMELCASE
)

public class RunCucumberTest extends AbstractTestNGCucumberTests{

    @Override
    @DataProvider(parallel = true)
    public Object[][] scenarios() {
        return super.scenarios();
    }
}
```
* Add the **Maven Surefire plugin configuration to the build section of the POM.**

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.0</version>
</plugin>
```
* Use the Maven *install* or a suitable command to execute the POM. This should run in parallel thread mode.

* To execute using a **Maven Failsafe plugin,** setup the POM as described in the JUnit section. Remove the parallel and useUnlimitedThreads settings in the configuration part.

* **The default thread count of the dataprovider in parallel mode is 10**. To change this the dataproviderthreadcount property needs to be added to the configuration section of the Surefire or Failsafe plugin in the POM.
```
<configuration>
    <properties>
        <property>
            <name>dataproviderthreadcount</name>
            <value>20</value>
        </property>
    </properties>
</configuration>
```

### Timeline Formatter

For a visual representation of threads, add the timeline report using the plugin option of CucumberOptions annotation on a JUnit or TestNG runner.

```
@CucumberOptions(plugin= {"timeline:<report folder>"})

```

### Running cucumber test using Maven

* You can run a single feature file by using cucumber.options which will override all the options you have in the @CucumberOptions annotation:

```
mvn test -Dcucumber.options="src/test/features/com/perspecsys/salesforce/featurefiles/Account.feature"
```

* At the same time, it's possible to do using POM:
```
  <build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>${maven-surefire-plugin.version}</version>
            <configuration>
                <includes>
                    <exclude>
                        **/CucumberRunner.java
                    </exclude>
                </includes>

```

Here is **/CucumberRunner.java - class that you will use as runner for passing all Cucumber options (@William mentioned about 'RunCukesTest' in my POM is CucumberRunner ) and of course you can use simple command like **mvn test** after POM configuration.





