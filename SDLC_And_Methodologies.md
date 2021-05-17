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
   
# Agile Implementation frameworks/principles:

1. **Scrum**
2. **Kanban**
3. **Xtreme Programming**

## 1. Scrum

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

## 2. Kanban

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
 
 #### Scrum vs Kanban

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

### 1. PI (Programme Increment).

* It's a timebox in which Agile release trains works on the objectives that are planned during the PI planning and delivers the product in the form of working, tested softwares and systems.

* The Program Increments (PI's) duration is usually of 8 to 12 weeks which consiststs of 5 working iterations of 2 weeks each and 1 iteration of Innovation and planning

* The pictorial view of PI is depicted below:
![SafeFlow](https://github.com/ambuj15/MyNotesHub/blob/main/Resources/Images/PI_FLOW.png "Safe Workflow")
![A simple flow](https://github.com/girirajvyas/101-series/blob/master/resources/images/sdlc/SAFe_Ceremonies.PNG "SAFe ceremonies")

### 2. PI Planning.

* It is the most essential part of Safe Agile in which different teams of ART's across the enterprise collects and get alligned to plan the work nfor the upcoming PI.

* It's the heartbeat of Safe and if you are not doing PI planning you are not followin SAFE.
* It usually occurs for 2 to 3 days in which different activities and ceremonies takes place. The different ceremonies that takes place are
  * **Business stake holder's presentation** on the grownth and achievements and more information about product, releases and expectations.
  *  **Breakouts** : In the breakout, teams estimate their capacity for each Iteration and identify the backlog items they will likely need to realize the features. Each team creates their draft plans on the basis of EPIC's received by the stake holder or Product Managers, visible to all, iteration by iteration.
  * **Draft Plan review :**During the tightly timeboxed draft plan review, teams present key planning outputs, which include capacity and load, draft PI objectives, potential risks, and dependencies. Business Owners, Product Management, and other teams and stakeholders review and provide input.
  * **Planning Adjustments:** Management presenting any changes to planning scope, people, and resources.
  * **BraekOut 2:** In this the team extends their previous day's agenda and create or modify existing draft plan as per the review comments received in plan review and planning adjustments.
  * **Final Plan Review:** This is final review of the draft paln presented by the team after planning adjustments and all.
  * **Program Risks and Dependencies:** A team shares the risks and dependencies if any to keep the stakeholder's aware that these risks and dependencies can impact their ability to meet the PI objectives.
  * **Vote of confidence:** At the end VOC happens in which each team member rates their confidence on the sacel of 1 to 5 and the average coming out of the VOC is marked as team's confidence to deliver their objectives.
  
  Each team conducts a ‘fist of five’ vote. If the average is three fingers or above, then management should accept the commitment. If it’s less than three, the team reworks the plan. Any person voting two fingers or fewer should be given an opportunity to voice their concerns. This might add to the list of risks, require some re-planning, or simply be informative. Once each team has voted the process is repeated for the entire ART with everyone expressing their confidence in the collective plan.
  * **Planning Retrospective :** A retrospective happens in which following points and inputs are expected from the teams in different ART's.
      a) What went Well
	  b) What didn't went well
	  c) Area of improvement for next planning.

### 3. Iteration Planning : 
The feature are taken in PI planning from the epic shared by the product manager and a product backlog is created for the team and for each feature multiple stories are written and groomed by PO. These stories are shared within the team and then the team discussion happens and stories are ellaborated and discussed within the team and then the estimations are done for each story. Then stories are picked by respective team members.

### 4. Iteration Retospectives : 
Occurs at the end of every iteration where discussion around what went well, what didn't went well and what needs to be improved happens.


**Key work items(Epic -> feature -> Story -> Task):**  
 - https://www.scaledagileframework.com/epic/
   - https://www.scaledagileframework.com/features-and-capabilities/
     - https://www.scaledagileframework.com/story/

**Note:**  "Epic has multiple features and is created by Product Manager" and "Features has multiple stories created by PO after discussion with stake holders" and "Story has Multiple tasks"

**Rally Status and Responsible for Action**  

|Sr. no| Status        | Responsible for Action                            |
|-----:| ------------- |:-------------:                                    |
|  1   | Unelaborated  | Product Owner writes the first draft                  |
|  1   | Defined       | After Sprint planning and after each team member agrees it is defined. i.e it can be worked upon                  |
|  1   | In Progress   | Create tasks on the first day and move to In Progress                  |
|  1   | Completed     | Mark complete once all tasks are completed and deployed                |
|  1   | Accepted      | After demo marked as Accepted by the Product owner                  |
|  1   | Ready to ship | Once feature is released                  |

**Feature Sizing**  

|Sr. no| Size (Tee shirt sizing)   | Story Points (Fibonacci series)     |
|-----:| -------------             |:-------------:    |
|  1   | XS                        |    15             |
|  1   | S                         |    30             |
|  1   | M                         |    45  (30 + 15)  |
|  1   | L                         |    75  (45 + 30)  |
|  1   | XL                        |    120 (75 + 45)  |
|  1   | 2XL                       |    195 (120 + 75) |

### 2.1 Agile Estimation Techniques:  

 > Estimation is one of the simplest, yet most frightening activities that software professionals face. So much business value depends on it. So much of our reputations ride on it. So much of our angst and failure are caused by it. It is the primary wedge that has been driven between business people and developers. It is the source of nearly all the distrust that rules that relationship.                                                                          - Robert C Martin (Uncle Bob)

 - **Planning Poker** 
   - All participants use numbered playing cards and estimate the items. 
   - There are free online tools as well that can be leveraged. 
   - Voting is done anonymous and discussion is raised when there are large differences. 
   - Voting is repeated till the whole team reached consensus about the accurate estimation. 
   - Planning poker works well when you have to estimate a relative small number of items (max 10) in a small team (5-8 people). 
   - Tip: try to keep the voting between affordable numbers.  Maximize the highest card to 13 points in case of 3 week sprint and to 8 in case of 2 weeks sprint.
 - **T-shirt Sizes**
   - This is a perfect technique for estimating a large backlog of relative large items i.e Features
   - Especially when you have several concurrent scrum teams working on the same product. 
   - Items are estimated into t-shirt sizes: XS, S, M, L, XL. 
   - The decision about the size is based on an open and mutual collaborative discussion. 
   - This method is an informal and quick way to get an rough feeling about the total size of your backlog.
   
 - **Dot Voting**
   - When you are faced with a relative small set of items and in need of a super simple and effective technique to estimate you can use Dot Voting.
   - This method has originated form decision making and you can use it for estimating.
   - Each person gets a small number of small stickers and can choose to vote for the individual items.
   - The more dots is an indicator of a bigger size.
   - Works well in both small and large group.
   - You have to limit the number of estimated items

 - **3 Point Estimation Technique**
   - In this estimation is done on the basis of 3 factors.
     - **Optimistic Approach/ Best Case :** No unkowns and end moment surprises
     - **Pessimistic approach/ Worst case :** Lot of unknowns, uncertainities and dependencies
     - **Most Likely/ Medium Case :** In this we have a jist of both optimistic and pessimistic approach.
   - Now the average of all three factors **for each task** is calclulated and confidence is committed on the basis of the average calculated.
   - The mean is calculated using the formuala:
     
     **E = Mean = (O + M + P) / 3** This is the mean calculated for the task.
   
   - Standard deviation is also calculated for each task and based on the difference between SD and Mean the confidence is calculated.

    **Standard Deviation (SD) = √ [((O − E)2 + (M − E)2 + (L - E)2)/2]**



# Questions and Answers

```
**Question 1:** When we should use Waterfall Model?
 **Answer:** 
 a) When the requirements are clear, well documented and fixed.
 b) Technology to be used is final.
 c) The Project is short and ample of resources with required expertise are there 
 
**Question 2:** What are different Agile metrics?
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
**Answer** In Safe multiple teams are involved who works on different trains but in agile a single team is there and all the
 planning and everything is centred and focused on that single team.

**Question 6)** Why the term train is used in Safe? Why not car, plain or scooter?
**Answer** My version : Bcz there is a pre-defined track on which a train with multiple boggies run. Similarly a release train runs on pre-defined set of tasks and backlogs distributed among multiple boggies/teams.

**Question 7)** What is Inspect and adapt in PI?
**Answer** 
* The PI is done when its timebox expires. Each PI concludes with a final system demo called a PI System Demo. This is a newsworthy event that illustrates all the features that have been accomplished during the PI. This is done as part of the I&A event, which is a regular time to reflect, apply problem-solving techniques, and take on improvement actions needed to increase the velocity, quality, and reliability of the next PI.
* The result of the I&A event is a set of improvement features or Stories that can be added to the backlog for the upcoming PI planning. In this way, every ART improves every PI.

** Question 8)** What are committed and uncommitted objectives?
**Answer:** The objectives which team will definitely cover in the PI are committed and the uncommitted one's are the one's which 
team keeps secondary objectives in case there are some impediments on committed one's.

**Question 9)** What is the difference between a feature and an objective?
**Answer:** An objective is given to a team but a feature can be shared between two or more teams and that feature will be part of 
objectives of both the teams separately.

**Question 10)** What is the difference between a spike and an enabler story? When do we create each?
Answer:
Spike: Spike is taken when we want to do any POC and it's outcome can be a document or a working code. (SPIKE=POC). There are no story points in SPIKE as it is considered as non-deliverable.
Enabler: Enabler is taken as a base for any future implementations. It is a deliverable and hence we consider story pointing and task burining under the same.

POC can or cannot be accepted as part of implementation in the project but enabler is surely something that you will definitely use in your project in future.

**Question 11)** How you estimate your stories? What are the metrices you follow?
Ans:
Story points are typically a unit of measuring three things, that each work item consists of:

The amount of work to do
The complexity of the work
Any risk or uncertainty in doing the work

**Question 12)** Is it wise to estimate the story on the basis of hours rather than complexity of the functionality?
**Answer: ** I my opinion it is not wise to estimate the story on hourly basis because a particular story can be completed by 
different individuals in different amount of time based upon their technical skills, speed and experience about the functionality. 
Hence i would recommend that estimation should happen on the basis of complexity and the amount of work taht needs to be done in a 
particular story.

**Question 13)** What is meant by Epic and how it is differnt from Features and stories? Who creates the EPIC?
**Answer:**

**Question 14)** What is meant by Metrics? What metrics are used in estimating the story?
**Answer** Metrics are pre-decided parameters which are used to measure how well an organisation is performing and progressing to 
achieve its objectives. It is basically defined in order to prevent or identify any deviations from the pre-defined objectives or goals.

I agile estimations are basically done on the basis of following factors:
1. Amount of Work
2. Complexity of work
3. Risks or uncertainities.


**Question 15)** If a new functionality is coming for testing purpose and you are completely unaware about it them how will you 
estimate it?
**Answer:**

**Question 16)** What is Definition of Ready and definition of done?
**Answer:** Definition of Ready defines a criteria which a particular user story has to complete before it get's up for estimation or inclusion in sprint.

The Definition of Done is an agreement between Development Team and the Product Owner on what needs to be completed for each user story.
Essentially, a DoD represents the acceptance criteria for a sprint or release
```

**Good Reads and questions:**
* https://github.com/Ashu-hub/All-About-Java/blob/master/MiscTopics.md
* https://github.com/girirajvyas/101-series
