# Questions and Answers

**1.** What is technical debt and what issue it causes in a code?

**Ans** 
* It's a direct result of a poorly written code.
* Technical debt is the outcome of any code which is written without following proper coding standards and also the code written needs to be refactored because of various problems in the code.
* Technical debt usually occurs when easy or limited solution is chosen over standard or better approach.

**_Issues caused by technical debts are:_**

- It makes software system slow
- It makes several functionalities unusable.
- You can face troubles in scaling/updating the project

**2.** What causes technical debts and what are different types of technical debts?

**Ans**

*_Causes of technical debts are:_**

- poor code review
- no use of static code analysis tool like sonar 
- poor test coverage
- bad development practices
- Use of outdated tools or technology

*_Different types of technical debts are:_**
- Source code formatting.
- Bad code review
- No or very less test coverage
- Lack of modularity
- Bad code design

> Sonar and Jacoco are the tools which can be used for code analysis and can help in eliminating technical debts

**3.** What is code quality?

**Ans** It's the desire to create a code that is easy to understand and work with.

**4.** Why you think code quality is important?

**Ans** Code quality is an important factor because the code you write should be understandable by the machine and the colleagues and different people involved or might get involved. If the code is not following proper quality standards then the machine can through an exception but when the humans will try to understand the code they might reach out to you again and again for understanding the code and hence dependency on you would be immense and also it is possible that in future you might not be able to understand the code you wrote yourself and hence code quality is an important factor.

Poor quality code can also result in:
- Increased maintenance cost
- Numerous software defects because of lack of knowledge of correct methods and all.
  Eg: Writing assertions in wrong way.
- Frustrated end user

**5.** What are different code quality metrics?

**Ans** Different code quality metrics are:

- **Complexity :** How complex your code is to understand.
- **Code Coverage :** How much of your code is covered by automation or unit tests.
- **Duplicacy :** How much duplicacy is there in your code
- **Coding style and standards :** It tells how clean is your code 
- **Code Smells :** A maintainability issue that makes your code confusing and difficult to maintain. IT a charcteristics of code  which indicates deeper problem.
eg:- to many comments, Duplicate codes, Lazy classes etc.
- **Bug :** A coding error that will break your code and needs to be fixed immediately.
- **Vulnerability :** A point in your code that's open to attack.

> **Note:** All the above mentioned metrices can be measured using static code analysis tool called as Sonar.

**6.** What is Cyclomatic complexity?

**Ans** It is the quantitative measure of the number of independent linear paths in the code. It measures the complexity of the program.

Ex:  If source code contains no control flow statement then its cyclomatic complexity will be 1 and source code contains a single path in it. Similarly, if the source code contains one if condition then cyclomatic complexity will be 2 because there will be two paths one for true and the other for false.

> **Use of Cyclomatic Complexity?**	
	- Determining the independent path executions thus proven to be very helpful for Developers and Testers.
	- It can make sure that every path have been tested at least once.
	- Thus help to focus more on uncovered paths.
	- Code coverage can be improved.
	- Risk associated with program can be evaluated.