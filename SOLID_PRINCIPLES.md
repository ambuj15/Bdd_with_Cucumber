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



