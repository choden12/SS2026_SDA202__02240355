# Class diagram & Object model
# Table of Contents
1. [Overview](#overview)
2. [Class_Diagram](#class_diagram)
3. [object_Diagram](#object_diagram)
4. [Challenges](#challenges)
5. [Lesson](#lesson_learn)
6. [Conclusion](#conclusion)
7. [Reference](#reference)
8. [link](#link)

## Overview
- The following is a report on the architecture of the design for an automatic grading and plagiarism checking system for the SWE class at the university. The design should be able to handle over 300 students every year, accommodate multiple submissions, have deadlines enforced, interoperate with the current mainframe-based LMS (requiring minimal modifications), have complete audit trails for the State inspectors, and also plagiarism detection (internal + TurnItIn) – on a shoestring IT budget.

- In order to convey the static structure and a specific running example of the system under consideration, two kinds of UML diagrams will be employed  **class diagrams** and **object diagrams** (or object models).

## class_Diagram
- class diagram is a blueprint of the system ststic structure.
![Class_Diagram](./images/part1.png)
![Class_Diagram](./images/part2.png)

##### Explanation
**Inheritance**: `Student`, `Professor`, and `Admin` extend `User`.
- **Association**:
  - Professor: creates Assignment.
  - Assignment: is related to GradingCriteria with cardinality  to 1.
  - Assignment: is related to Submission with cardinality 1.
  - student: is related to Submission with cardinality 1.
  - Submission :is related to Grade with cardinality 1 to 0..1.
  - Submission: is related to PlagiarismReport with cardinality 1

  ## object_diagram
  - is a snapshot of the system at a specific moment.
  ![object](./images/object.png)

##### Explanation
- Re-attempts: are permitted (attempt 3).
- Compliance check – submission at 20:15 occurs before deadline, hence valid.
- Grading procedure: results in scoring with extensive feedback provided.
- Check for plagiarism: is carried out (internal + TurnItIn).
- Tracking the attempt: is recorded.
- Learning Management System: (objects not shown) would output the mark to the mainframe using batch process.

## challenges
- It was very difficult for me to decide on what classes to put. I had many different entities that could be included in the ER Diagram such as User, Student, Professor, Admin, Assignment, Submission, Grade, PlagiarismReport, AutoGrader, TurnItInAdapter, and LMSAdapter. It was very difficult for me to strike a balance between being complete and simple.

## lesson_learn

1. **Audit logs should be planned from day one** – It is difficult to retro-fit auditability into a project. Having an immutable, timestamped log is easy and complies with regulations.

2. **Multiple attempts are not a bug; rather they are a feature** – Allow students multiple tries without storing unnecessary data. The benefits outweigh the cost by far.

3. **Loose coupling using adaptors** – With isolation of the LMS and TurnItIn behind adaptor layers, the internal grading logic will never need revision no matter how external systems evolve.

4. **Describe the runtime snapshot** – A description of object graph in textual format can be very useful when trying to explain the system behavior to the profs.

## Conclusion
- Class Diagram and Object Model describe a comprehensive and economical solution to meet all of the required criteria. Automation of grade checking will involve the use of free test runners, and AuditLog will ensure persistent and traceable grades. Plagiarism will be checked internally and via TurnItIn under a cost constraint. Integration of Learning Management System will be done via batch files without touching the mainframe code. Deadline is set using Assignment.dueDateTime, and Submission.attemptNumber allows an unlimited number of tries. Grade rules can be configured flexibly by defining them in JSON format. 

## reference
GeeksforGeeks. (2025, August 29). Unified modeling language (UML) class diagrams.
https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/

GeeksforGeeks. (2025, January 3). Unified modeling language (UML) object diagrams.
https://www.geeksforgeeks.org/system-design/unified-modeling-language-uml-object-diagrams/

## Link
draw.io: https://app.diagrams.net/#
