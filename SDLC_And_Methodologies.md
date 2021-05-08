## SDLC (Software Development Lifecycle)

* **SDLC* is a systematic process of developing a software. It has various cycles or phases:

1. **Planning and Requirement Analysis** : In this phase various parties like customer, product owners etc sit together and gathers the requirements and do neccessary plannimg whic involves **quality assurance requirements**, **risks**, **what technologogy stack to be used**, **team size** etc, are planned.

2. ** Defining the requirements** : In this phase the requirements gathered during plannimng stage are analyzed and then drafted and then they are sent for review and approval of the stake holders.
Generally the outcome of this phase is **SRS document.**

3. **Software Design :** In this phase the information gathered from above two phases is used and a software design (the design architecture which will be used) is created and is drafted in a document called **DDS - Design Document Specification.**

4. **Development** : When the DDS is reviewed and approved by various architects and stake holders this DDS is utilized and actual software development starts. This is the phase which yields a working application.

5. **Testing** : In this phase the quality of the product created in the last phase is tested. This phase can have multiple sub-phases like Unit testing, Integration testing and Functional testing.

6. **Deployment** : Now as the testing is done and the product has gone thru multiple checks it's the time to deploy the product. It can be directly deployed to the production and can also be deployed or released for UAT or certification to do one more quality check as end user.

7. **Documentation** : This is optional phase some company follows some not. In this a document containing various details of the product are drafted.

8. **Maintenance** : In this phase the developing team gives the support to the user in case there is some code failure in production or some functional support is required.


# SDLC Models

Following are the different SDLC models:

1. Waterfall
2. Agile
3. Iterative
4. Spiral
5. Devops
6. Others
 6.1 Lean (Originally Used By Toyota in Manufacturing)
 6.2 Safe (Use both agile and lean techniques)
 
 We will only cover Waterfall, Agile and Safe in detail as these are most used ones.
 
 ## 1. Waterfall 
 
 * In this methodology each phase should begin after the completion of previous phase.
 * All the phases we discussed above in SDLC are implemented here step by step in linear form and hence it is also called as **linear-sequential life cycle model**
 

**Pros:**

* Easy to understand and Simple to manage
* Can only move on to the next step when the previous one is completed.
* Process and results are well documented.

**Cons:**

* This model doesn’t work well if flexibility is needed or if the project is long term and ongoing.
* lack of flexibility in changing scope during the development process
* Limited in speed as the progress is dependent on completion of previous stage.

 ## 2. Agile  
* Agile is an Iterative approach of project management and software development that helps teams to deliver values to their customer faster and in effective way.
* Unlike waterfall in agile there is a flexibility to change the requirements in the product.
* Instead of betting everything on a **"big bang"** launch, an agile team delivers work in small, but consumable **increments**.
* Requirements, plans, and results are evaluated continuously so teams have a natural mechanism for responding to change quickly.
* It focuses on getting something workable in front of users as soon as possible and then working on improvements.
* Focus is on the interactions between the users and developers, and developers work closely together to reduce feedback loops.

**Values of Agile**

* **_Individuals and interactions_** − In Agile development, self-organization and motivation are important, as are interactions like co-location and pair programming.

* **_Working software_** − Demo working software is considered the best means of communication with the customers to understand their requirements, instead of just depending on documentation.

* **_Customer collaboration_** − As the requirements cannot be gathered completely in the beginning of the project due to various factors, continuous customer interaction is very important to get proper product requirements.

* **_Responding to change_** − Agile Development is focused on quick responses to change and continuous development.


**What are the Merits and Demerits of Agile?**

1. **Merits:**
   
   * Flexibility: Agile provides flexibility of continuous delivery and product improvement and hence the product which is delivered finally is as per the latest market standards.
   * Teamwork : In agile the whole team participates from the beginning to end of the product delivery and hence most of the members are on the same page which helps in ellimating gaps.
   * Demo's : This is one thing which helps the team members to showcase their skills of presenting their product to clients and stake holders which is good for the members in the longer run. It also build satisaction in customer
   * Continuous improvement : As we work in sprints and hence at the end of each sprint we have the results of our performance iast sprint and hence this helps in continous improvement by learning from past experience sprint by sprint.
   * Parallel working : Unlike waterfall testing and development team works in parallel.
   
2. **Demerits:**

    * Sometimes flexibility lands into problem because frequent changes causes replanning and re-pointing of stories.
	* Dependency of customer input sometimes acts as a blocker and hence team sits idle.
	* No or less focus on documentation in agile and hence sometime it is hard to anwer that what and why particular thing is developed.
   
### Agile Implementation frameworks/principles:

1. **Scrum**
2. **Kanban**
3. **Xtreme Programming**

#### 1. Scrum

* It is an agile implementation framework which works on iterative approach(means iteration or sprint wise) within a small team of 8 to 10 members
* The team constitutes of :
  
  **a)** _Scrum master_ : Responsible for setting up of team, srum meetings, removing the issues and impediments faced by the team.
  **b)** _Product Owner_ : Gathers requirements and finalize them, creates backlogs, takes demo's and is responsible for delivering and accepting the stories at the end of each iteration.
  **c)** _Scrum team_ : The members in the team including developers and testers who works on the stories they have pulled in their name from the list of stories in the iteration and also demoe's the story to the PO.
  
* A scrum team has a **Product Backlog** which acts like a repository and contains all the user stories that a team is going to deliver in multiple sprints. This backlog is maintained by PO and is shared within the team. Team is free to ask PO to add, update or delete the requirements from the backlog.

**Process Followed in Scrum**

1. The PO creates a backlog after discussion with stake holders and scrum team.
2. During each Sprint, top user stories of Product backlog are selected and turned into Sprint backlog.
3. Then the story grooming session happens where the stories and the functionalities are explained and the story pointing is done using different methodologies which we will cover later.
4. Now post grooming planning happens where the stories allocation happen, **scrum follows push based system** because in Scrum you plan your production in advance based on a prediction of productivity for a given period of time. That is push.
5. Then sprint starts and team start working on their respective story which they have to complete as per the points decided.
6. Everyday a scrum meeting happens which is an informal connect of 15 mins max where each team member shares there progress and impediments if any which are resolved by SM later.
7. At the end of the sprint team delivers the functionality and gives the demo to the PO in case of functiolnal stories and to tech architect in case of technical stories.
8. Review and retrospective: Sprint Review and Sprint Retrospective
9. Extension: Backlog refinement and Scrum of Scrums

#### 2. Kanban

* It is the second and very popular agile implementation framework which has following main points:
 
 a) In kanban no filxed timelines are there like scrum sprints it is a continuous flow
 b) No fixed planning and meetings like DSM
 c) No task estimations
 d) No scrum master
 e) No sprint backlogs
 
* In Kanban a board is maintained and a ticket based work is done. All the tasks are listed down under to-do, the tasks which are in progress are under doing and completed tasks are kept under done.

* The tasks are completed and progressed on daily basis, the team members sets the daily goal and takes the work on priority basis.

* A very good example of Kanban is restaurant kitchen. There a ticket based system is there in which all the fresh orders are kept in To-Do, in progress orders are kept in doing section and completed orders are kept in done.

* One more interesting thing about kanban board is **LIMIT**. You can set the limit of the tasks that can be taken under To-Do. It's not that whole backlog will fall under To-Do. We can set limit that at a time only specified number of stories or tasks can be accomodated in To-Do section from the backlog and as tasks start moving the stories can be picked from backlog.
 
 ##### Scrum vs Kanban

|Sr. no| Scrum                                              | Kanban                                            |
|-----:| -------------                                      |:-------------:                                    |
|  1   | well defined work; takes limited work              | its dynamic, can take extra work                  |
|  2   | immutable                                          | mutable                                           |
|  3   | time over burden                                   | focuses on continuous delivery                    |
|  4   | Structured and clear with goal                     | not structured but clear with goal                |
|  5   | Good number of meeting (planning, standup are must)| not a lot meeting (stand-up is not required)      |
|  6   | intervals ; sprint time                            | no intervals, work can be chosen on a daily basis.|
|  7   | more process, more overhead                        | less process and less overhead                    |
|  8   | good for new team and new project                  | for mature team                                   |
|  9   | Sprint velocity is 2 weeks                         | No specific timelines                             |
|  10  |Teams should strive to not make changes to the sprint forecast during the sprint.Doing so compromises leanings around estimation.            | Change can happen at any time                             |
|  11   | Release at the end of Sprint if approved by PO    | Continuous delivery or as per team's discretion    |

# Safe Agile (Scaled Agile Framework)

* It is a set of organizations and workflow patterns intended to guide enterprises for scaling lean and agile practices. Basically SAFE comes into picture when large number of teams are involved in a project and each one of them are using their own way of agile but failing consistently.

* SAFe promotes alignment, collaboration, and delivery across large numbers of agile teams.
* It follows the process of lean agile and scrum.
* All SAFe teams are part of one or other Agile Release Train (ART).
* In Program level, Value of SAFe is delivered by long-lived Agile Release Trains (ART). Iteration is for team and train is for the program.
* Agile Release Trains (ART) is the primary vehicle for value delivery at the program level. It delivers a value stream to the organization.
.

## Ceremonies in SAFE.

#### 1. PI (Programme Increment).

* It's a timebox in which Agile release trains works on the objectives that are planned during the PI planning and delivers the product in the form of working, tested softwares and systems.

* The Program Increments (PI's) duration is usually of 8 to 12 weeks which consiststs of 5 working iterations of 2 weeks each and 1 iteration of Innovation and planning


# Questions and Answers

**Question 1:** When we should use Waterfall Model?
 **Answer:** 
 a) When the requirements are clear, well documented and fixed.
 b) Technology to be used is final.
 c) The Project is short and ample of resources with required expertise are there 
 
**Question 2:** What are different Agile metrices?
**Answer:**

**Question 3:** What you like and dislike about scrum?
**Answer:** 
**What I like about scrum is:**
* It facilitates the product delivery at faster pace.
* One can see code functioning pretty soon as parts of functionality gets delivered in small chunks as compared to waterfall.
* Scrum ensures effective use of time and money
* Large projects are divided into easily manageable sprints
* Lot of team coordination is there in scrum as developer and testers sit together and small functional issues are resolved at very faster pace because of good communication between scrum members
* All round of development of resources happens because developer and testers have idea about each other's work.

**What is that don't like about scrum is:**
* In case any of the member is non-performing there are high chances of commitment and project failures as each individual is solely responsible to perform the task but if something fails it's responsibilty comes to the scrum team.
* Daily meetings could be cumbersome sometimes.

**Question 4)** Please describe the way of adaptation of new employees on your project. What is the main steps of this process. How do you know that candidate is ready for production? Below are the points by which we make the journey of new joinee comfortable.

**Answer**
1) Explain Who is who, how to use office equipments, who is the right person for the query resolution of each department.
2) Address any queries or doubts raised on Organization guidelines, norms, culture and unwritten rules.
3) Sharing insight on how things are done in the organisation.
4) Introducing the new associate to team members.
5) Able to expalin work related tasks.
6) Making aware them about the Org level trainings, portals etc.

In your project:
1. Ensures his Id is created on the portal.
2. Ensures we raised all the requests for necessary resources like laptop,headphone etc.
3. Ensures he gets all the permission to access to the system.
4. Making aware of the all mandatory trainings of the project.

**Question 5)** How safe is different from regular agile?
**Answer** In Safe multiple teams are involved who works on different trains but in agile a single team is there and all the planning and everything is centred and focused on that single team.

**Question 6)** Why the term train is used in Safe? Why not car, plain or scooter?
**Answer** My version : Bcz there is a pre-defined track on which a train with multiple boggies run. Similarly a release train runs on pre-defined set of tasks and backlogs distributed among multiple boggies/teams.