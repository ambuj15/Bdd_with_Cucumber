# Clean Design

 

* It is an approach to develop a code which is easy to understand and reuse

* Clean design can be implemented using different priciples and **SOLID** is one of them

 

# SOLID PRICIPLES

 

## S : Single Responsibility Principle

## O : Open-Closed Principle

## L : Liskov's Substitution Principle

## I : Interface Segregation Principle

## D : Dependency Inversion Principle

 

 

# Single Responsibility Principle

 

* It states that a class should have only and only one reason to change meaning a class should have only one responsibility.

 

  - **Example**

 

```

  public class Employee

{

    private String firstName;

    private String lastName;

    private LocalDate hireDate;

    private HashSet<Employee> subordinates;

 

    public Employee(String firstName, String lastName, LocalDate hireDate) {...}

    public void addSubordinate(Employee subordinate) {...}

    public void removeAllSubordinates() {...}

    public void print() {...}

}

```

**Question 1:** Which method from the code above adds one more responsibility to the Employee class?

**Ans** Print method and hence this is violation of Single responsibility principle.

 

* In above example you see that print method is adding a responsibility to the employee class which is created to initiate employee only. The ideal approach could have been:

 

 

```

  public class Employee

{

    private String firstName;

    private String lastName;

    private LocalDate hireDate;

    private HashSet<Employee> subordinates;

 

    public Employee(String firstName, String lastName, LocalDate hireDate) {...}

    public void addSubordinate(Employee subordinate) {...}

    public void removeAllSubordinates() {...}

    new Print().print();

}

 

public class Print{

 

public void print()

{

System.out.println("Data to print");

}

}

```

 

**Question 2:** Use the code snippet and its description below to answer the question that follows.

 

```

public class Account {

    public Double calculateBalance() {...}

    public void save() {...}

}

```

 

The Account class in an accounting application has two methods:

 

- calculateBalance, which makes a calculation based on Account's data;

- save, which stores Account in some database.


Does the Account class’ design adhere to the Single Responsibility Principle?

 

**Answer** No. Because, The Account class violates the SRP because it has more than one reason to change. **Save is a persistence responsibility**, while **calculateBalance is an accounting responsibility.** Therefore, the persistence functionality should be located in a different class or module.

 

* Another Example of SRP:

 

**Class BEFORE SRP:**

 

```

public class Order {

    public Double calculateTax() {...}

    public void applyPromotions() {...}

    public Stock checkItemsAvailability() {...}

    public String describeOrder() {...}

}

```

 

**Class after SRP**

 

```

public class ... {

    public Double calculateTax() {...}

}

public class ... {

    public void applyPromotions() {...}

}

public class ... {

    public Stock checkItemsAvailability() {...}

}

public class ... {

    public String describeOrder() {...}

}

```

 

## Points to remember while following SRP.

 

* A class should have high cohesion (Is the degree to which various parts of a software components are related). A high cohesive class is the one in which all the methods in the class uses all the fields defined in the class.


**Example of Low and high cohesion**

 

```

public class square{

               int side = 2;

               public int calculateArea(){

                             return side*side;

               }

               public int calculatePerimeter(){

                             return side*4;

               }

 

               public void draw(){

                              if(highResolution){

                                             //Render high Resolution image

                              }

                              else{

                                             //render real image

               }

              

               public void rotate(int degree){

                              //rotate the image clockwise by specified degree.

               }

}

```

 

> The above code has very low cohesion overall. calculateArea and calculatePerimeter are closely related(and high cohension),draw() and rotate() are

> interelated (high cohension), but overall they cohension is low.

 

**Solution to above problem**

 

```

public class square{

               int side = 2;

               public int calculateArea(){

                             return side*side;

               }

               public int calculatePerimeter(){

                             return side*4;

               }

}

 

// Respponsibility :- Measurement of Square

 

public class squareUI{

               public void draw(){

                              if(highResolution){

                                             //Render high Resolution image

                              }

                              else{

                                             //render real image

               }

              

               public void rotate(int degree){

                              //rotate the image clockwise by specified degree.

               }

}

// Respponsibility :- Rendering of image of square.

```

>>So we can safely say that 1st class square has responsibility related to measurement of square.

>>Similary 2nd class is related to rendering images.

 

* Coupling should be minimum i.e a code should be loosely coupled (Coupling is defined as the level of inter-dependency between various software components)

 

# Open-Closed Principle

 

* It aims to create flexible code that allows for future changes that do not impact existing code, hence meaning **Open to extension but closed to Modification**

* You should be able to change one feature without altering others.

* The best way to implement open closed principle is that:

- Implement new functionality on new classed and inherit the original base classes

- Create interfaces or abstract classes

 

## Why open closed principle should be followed:

 

* If you don't follow OCP then developers might have to test the whole functionality as part of unit testing

* Chances of regression failures will definitely increase

* **If OCP is not followed and you are adding additional functionality to the existing class you are violating SRP also because you are making a class to perform more than one functionality.**

 

## Implementation of OCP:

 

>Refer the following link : https://github.com/Ashu-hub/All-About-Java/blob/master/SOLID.md#open-closed-principle


# Liskov Substitution Principle

* It goes like **Objects should be replaceable with their subtypes without affecting the correctness of the program.**
* **Definition** If S is sub type of class T then the objects of class T should be replaced with the objects of class S.
* **Easy Explaination**
   * If there is a class called Animal and having an object A and there is a class called dog which is derived from the class Animal and have object as D, then as per LSP you must be able to use the D object everywhere in place of object A without hampering any functionality.
   * **Child class object can be used as the substitute of the objects of the Parent class.**
   
* The LSP focuses on “IS SUBSTITUTABLE FOR A” rather than “IS A. relationship”

> Classes extending BasicTestCase uses Liskov's Substitution principle in my framework.

## Bad example
```
public class Bird{
    public void fly(){}
}
public class Duck extends Bird{}
// The duck can fly because it is a bird, but what about this:

public class Ostrich extends Bird{}
// Ostrich is a bird, but it can't fly, Ostrich class is a subtype of class Bird, but it shouldn't be able to use the fly method, 
// that means we are breaking the LSP principle.

```
## Good example
```
public class Bird{}
public class FlyingBirds extends Bird{
    public void fly(){}
}
public class Duck extends FlyingBirds{}
public class Ostrich extends Bird{} 
```

>**Reference for one more car example:** https://github.com/Ashu-hub/All-About-Java/blob/master/SOLID.md#liskov-substitution-principle

# Interface Segregation Principle

* The principle of ISP is that **No client should  be forced to depend on methods that it does not use.**
* According to this principle an interface shoul be designed keeping the client's need in mind.
* Developers that adhere to this principle typically favor **thin—or small—interfaces instead of fat—or big—interfaces**.
* The goal of the ISP is to reduce the effects and regularity of changes, which you accomplish by developing thin interfaces and splitting software into independent parts.
* Create small interfaces which should focus on implementation of similar sort of functionality rather than diversity of functionalities.


## Benefits of Interface Segregation Principle:

* It decouples the application because in this you create small interfaces which focuses on similar functional behaviours and hence reduces inter-dependency between various components.
* Increases cohesion and hence simplifies the functionality
* Increases testability of the application

>Keep in mind that interfaces that adhere to the ISP minimize the impact of changes, while interfaces that do not adhere to the ISP 
>increase the risk that a change will impact other aspects of the software.

## Tips to apply ISP:

- Ensure class implements all methods of an interface. This will refrain you from adding unwanted and unneccessary methods.
- **Make Interface Cohesive** : 
   - Thin interfaces should be cohesive, which means they contain groups of operations that logically belong together. Ensuring cohesion prevents a sub-optimal, one-method-per-interface design in a solution.
- Divide and combine fat interfaces.

> **Reference of the implemented code** 
>https://github.com/Ashu-hub/All-About-Java/blob/master/SOLID.md#interface-segregation-principle

# Dependency Inversion Principle

* As per this principle **High level module should not depend on low level module . Both should depend on Abstraction.**
* Abstraction should not depend on details but details should depend on abstraction.

> Take example of the gateway which acts as an abstraction in which the merchant like Stores, Amazon, Flipkart do not directly 
>interact with the banks but they interact with them through some gateway. And different wallets also interacts with gateway only and>not tightly coupled with the banks or merchant.

* In this we introduces and abstraction layer between the different systems which acts as a mediocre by facilitating the interaction between high level and low level system and details.

* When you follow DIP you simply avoid unneccessary code changes and updates to your code if any changes to details or any dependent classes are made. It promotes loose coupling.

*  As you apply the principle, it’s also essential to **recognize and avoid a database dependency.**

> Good references : https://medium.com/@kedren.villena/simplifying-dependency-inversion-principle-dip-59228122649a
> https://github.com/Ashu-hub/All-About-Java/blob/master/SOLID.md#liskov-substitution-principle

# Avoiding DB dependencies using Dependency Inversion Principle

* **Anti-patterns** are certain patterns in software development that are considered bad programming practices.
* **_One anti-pattern that violates the DIP is a database dependency._**

* The pictorial representation of hard dependency of business layer on Database here can be treated as detail. The image represents anti-pattern.

![Anti Pattern](https://github.com/ambuj15/MyNotesHub/blob/main/Resources/Images/DIP_Database1_With_Anti_Pattern.png "Anti-Pattern a violation of DIP")

  -  In this application design, the Presentation layer depends on the Business layer. Then the Business layer depends on the Data Access layer, which depends on a specific Database.
  - It violates the **DIP because the database is the storage mechanism of the system, and it is a detail. High-level business logic should not depend on this detail**. 
  - There is a hard dependency on DB.

* Now to overcome this database dependency or ant-pattern

![Eliminating DB dependency](https://github.com/ambuj15/MyNotesHub/blob/main/Resources/Images/DIP_Database1_Without_Anti_Pattern.png "Eliminating Anti-Pattern/DB dependency")

   - **The Business logic should not be dependent on the database or dependent on the schema or tables in the database**. It also should not be concerned with whether the systems are backed with Oracle, MySQL, or a File system. These are all elements you can abstract away to keep the architecture as clean as possible.
   - In the example diagram above, the Business logic only depends on the Business Objects and a set of interfaces to communicate with other layers. Hence introducing an abstraction layer between business logic and the detail and hence eliminating Anti-Pattern or hard dependency

# Some other design Principles.

## 1. DRY (Don't repeat yourself)

* Every piece of knowledge or logic must have a single, unambiguous representation within a system.
* This principle aims at reducing or completely eliminating repetetive codes.
* To achieve DRY:
  -  divide your codes into smaller pieces and chunks and try to write the methods/functions for different functionalities and re-use them instead of re-writing them again and again.
  - Don't write lengthy methods, but divide logic and try to use the existing piece in your method.
* An example of dry is the utility, helper and wrapper classes we create like some of the methods we have created to identify we elements using X-paths. In those methods we don't write the code driver.findElement(By.xpath) again and again we just call the wrapper method where we want to find the method using Xpath.
* The concept of state sharing using **PIKO container in cucumber also aims at implementing DRY principles** so that multiple step definition classes can interact with each other and can share common steps among them.

**Benefits**
* It helps you create a short code which is easy to maintain, re-use, debug and chances of bugs are also reduced.
* Saves a lot of time because you are not writing same logic again and again.
* Improves code-readability.
* Avoid redundant repeated code

## 2. WET (Waste Everyone's time or We enjoy Typing)

* The violation of DRY principle results in WET principle.
* In this long redundant codes are written and all the principles of DRY are violated.

## 3. KISS (Keep it simple stupid)

* It aims at keeping the code simple short and easy to understand.
* Keep your methods as small and as simple as possible.
* **Each method should solve only one problem.** If you have multiple use cases then try to divide them in small chunks so that code becomes simple and easy to understand.

* **In the below code snippet see the second solution is better approach**

```
public String weekday1(int day) {
    switch (day) {
        case 1:
            return "Monday";
        case 2:
            return "Tuesday";
        case 3:
            return "Wednesday";
        case 4:
            return "Thursday";
        case 5:
            return "Friday";
        case 6:
            return "Saturday";
        case 7:
            return "Sunday";
        default:
            throw new InvalidOperationException("day must be in range 1 to 7");
    }
}

public String weekday2(int day) {
    if ((day < 1) || (day > 7)) throw new InvalidOperationException("day must be in range 1 to 7");

    string[] days = {
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
        "Sunday"
    };

    return days[day - 1];
}
```
* Violation of kiss leads to unncessary investment of time in understanding lengthy and complex code in case you or some other developer needs to work on it.
* Suppose you have written a code by violating KISS design principle and in future you identified a problem and you or one of your team is assigned to solve this problem. Now, **Can you identify the problem and understand your code and know what it’s actually trying to do?.**

## 4. YAGNI (You ain't gonna need it)

* Under this principle refrain yourself from adding extra code on the basis of anticipation that you might need it in future.
* You should only implement what is the need of the hour even if you are sure that you’ll need it in the future. You implement only what’s needed at this moment, under the current requirements.
* Adding code on the basis of anticipation or assumption or surity too that the feature will be introduced in future is not at all recommended and it's a waste of time, effort because who knows, maybe these features that you think you will need it, it will be changed then, or not needed at all.
* Adding extra features, means adding more code to write, to maintain, to test and debug.


> References: 
* https://dzone.com/articles/software-design-principles-dry-and-kiss#:~:text=The%20DRY%20Principle%3A%20Don't,unambiguous%20representation%20within%20a%20system.%22
> * https://medium.com/omarelgabrys-blog/object-oriented-analysis-and-design-design-principles-part-6-b78e2b9da023
> * https://medium.com/@nrk25693/dry-or-wet-and-why-867ac3096483
# Questions and Answers:

1. Why we should follow solid principles?
Ans : We should follow solid principles because, if we don't ollow it we may end up with:

   - A tightly coupled code with different modules and applications.
   - Tight coupling causes time to implement new functionalities , features and bug fixes and sometimes results in introducing new issues 
   - End up with a code which is non testable
   - Code duplication could happen
   - End up with introducing regression issues along with many unkonwn problems which are really difficult to debug.
   
 If we follow solid priciples then:
 
  - **We will reduce tight coupling** (Coupling is defined as the level of inter-dependency between various software components.) and hence a good quality code will be achieved.
  - **A highly cohesive** (is the degree to which various parts of a software components are related. or it is a **degree of relation.**) code will be created
  - Makes code more readilble, extensible and maintainable.
  
2. What factors or metrices should be followed while creating an application?
Ans : An application should be developed by keeping in mind 3 major factors:

  - **Architecture:** Chosing the right architecture based on the requirements is the first step in application development. Eg: MVC, WEBAPI, Spring-Boot
  - **Design Principles:** Choosing the right design principles helps in increading code maintainibility, extesibility and readability.
  - **Design Patterns:** We need to chose correct design pattern to build the software.
  
3. How to achieve KISS?
Ans: To achieve KISS:
     
- Try to write simple code.
- Think of many solutions and identify the best one out of them.
- Whenever you find lengthy code, divide that into multiple methods


