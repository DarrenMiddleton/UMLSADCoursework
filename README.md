# Project Task: #

### Specify the following system as a class diagram and use cases in UML-RSDS:###

The system is intended to do release planning for an agile development process. The development or modification work to be 
done is divided into a number of **Story** objects, which have
a storyId : String unique key. Each story has an ordered list subtasks of **Task** objects, which
define particular work tasks. Tasks have a unique taskId : String key, and an Integer duration. A
task may depend on other tasks (which must be completed before it is started). A task has a set,
needs, of **Skill** objects which represent skills needed to carry out the task. In turn, a Skill has a
unique skillId : String. An entity type **Staff** represents staff, and has a unique staff Id : String,
and an Integer costDay. A set, has, of skills is associated to each staff object. Finally, the task
schedule for an iteration is represented by a class **Schedule**, with an attribute totalCost : Integer,
and an ordered list assignment of **Assignment** objects, where each Assignment has associated
staff and task objects.


The required system operations are:


1. *allocateStaff* : for each unallocated task **t**, all of whose dependsOn tasks have already been
allocated, find an available (unallocated) staff member who has all the skills required by **t**,
and assign the task to the cheapest such staff member, **s**. Create a new assignment for **t** and
s, and add this to the schedule.
2. *calculateCost*: add up the products **s.costDay x t**.duration for the assignments of the schedule
and add this to the totalCost of the schedule.
3. *displaySchedule*: print the list of assignments, with information of the staff Id, costDay,
taskId, duration for each assignment.


Evaluate your solution on several test cases of planning problems (the files in.txt, in1.txt,
in2.txt in output.zip on Keats). Does your approach always find the schedule with lowest total
cost? How efficient is your solution on large problems (test100.txt, test200.txt, test500.txt)?
Identify ways to improve your solution.


Add a duration : Integer attribute to Schedule, and compute this as part of the calculateCost
operation. [hint: define a recursive operation totalDuration() : Integer of T ask which calculates
the duration of the task together with those it depends on]
The system only calculates a schedule for a single iteration: the iteration is complete when all
possible allocations to available staff have been made. Define a use case nextIteration to continue
the schedule with a further iteration. No new classes or attributes are needed, and the use case
itself has a single, very simple, constraint on Schedule or on Assignment.