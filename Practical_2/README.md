# UML & Use case Diagram
# Table of Contents
1. [Overview](#overview)
2. [Part1](#part1)
3. [Part2](#part2)
4. [part3](#part3)
5. [Challenges](#challenges)
6. [Conclusion](#conclusion)
7. [Reference](#reference)
6. [Link](#link)

## Overview
- This practical outlines the design of an automated grading system for programming assignments in a university Sotfware Engineering course. Where system is intended to replace the current manual process and address the challenges of scalling to 300+ student or user per year, the key goals include automation of grading, plagiarism detection, integration with university learing management system.

#### Before entering directly into the main part, i had identified the actors and there roles, those are;
Student: To submits code, checks result and resubmits.
- Professor: To sets deadline, grading policy and evaluates grades.
- System: To executes grading process, plagiarism checking and storage.
- Turnitin: External service for plagiarism checking.
- LMS: To keeps final grades.
- Admin: To manages system.
- Auditor: To analyzes audit logs.

- The design is presentend through three complementary diagram:

## Part1
###  Interaction Overview(IoD) from an Actor-to-Actor perspective
![IOD](./images/IOD.png)
### Explanation
- In diagram above, it can be observed that for successful completion of the business process, there is a need for a closed-loop cycle wherein the professor sets the rules, the students enter their code before the deadline, there is automatic grading, plagiarism detection through Turnitin, and finally result publishing in the LMS. The auditor has the option of reviewing the entire audit trail afterwards.

## Part2
- Use Case Diagram describes the system boundaries along with the exact functionalities for carrying out the interaction process mentioned above. The actors in this diagram consist of Professor, Student, Auditor, and turnitin, as well as LMS systems.
![UCD](./images/UCD.png)

### Explanation
- The instructor provides definitions of deadline and grading rubrics.
- Students submit source code, with unlimited attempts till the deadline.
- The system does not accept any submission after the deadline.
- The system analyzes the source code according to rubrics and assigns an initial score.
- The system analyzes similarities between submitted sources compared to others and to sources at Turnitin.
- Students receive their final score along with the feedback.
- Once finalized, scores are uploaded to the mainframe-based LMS.

## Part3
- This diagram combines the previous views, showing how actors interact through the system to accomplish the business outcome. It uses a swimlane format to clarify responsibilities.
![FINAL](./images/FINAL.png)
![FINAL](./images/FINAL1.png)

### Explanation
##### The sequence diagram illustrates the full flow:
- The professor establishes the assignment prior to its allocation.
- The Several submissions are possible, and the system handles the deadline enforcement, grading, and submission scanning through Turnitin.
- The professor assesses all results, makes the required changes, and launches the grade synchronization process to the LMS that is mainframe-based but requires just a one-way push.
- Access to the audit trail is available to the auditor independently.
- Such setup ensures that all actions will be logged and, thus, meets the requirement of auditability.

## Challenges
- In the process of developing the Interaction Overview Diagram (IoD) for the automated grading system, I had to deal with certain difficulties. Among the difficulties I faced during the process were those related to how I can get an understanding of the interactions between all the actors involved in the process. Among the actors involved in the process are the students, the professor, the automated grading system, the LMS used by the university, and external agencies like Turnitin. Thus, I had to gain an understanding of how these actors interact among themselves in order to meet the business objective.

- Moreover, I faced difficulties in organizing the sequence of interaction as I had to make sure that the flow began with the perspective of business outcomes and then proceeded with actor-to-actor interaction.

## Conclusion
##### The Automated SWE Grading System proposal will meet the requirements of the university with respect to scalability, integrity, and auditability within budget and infrastructural limitations. The three figures demonstrate:
- Interactions between actors that generate the business value.
- The decomposition of functionality into use cases.
- Interactions at the system level that implement the use cases.

- Through automated evaluation and plagiarism prevention, the system allows faculty members to avoid repetitive processes, ensures quick feedback to the students, and enables maintenance of a full audit trail. Such a structure makes an excellent basis for integration into the university environment.

## Reference
- GeeksforGeeks. (2025, July 23). Interaction overview diagrams | Unified Modeling Language (UML).
https://www.geeksforgeeks.org/interaction-overview-diagrams-unified-modeling-language-uml/
- Visual Paradigm. (n.d.). What is interaction overview diagram?
https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-interaction-overview-diagram/


## Link
- Deepseek: https://chat.deepseek.com/a/chat/s/c5cf15d4-1ff0-44f3-b3ca-ba08805b0f55 
- Draw.io: https://app.diagrams.net#G1Ir7RZhGqwMTBU94pyYJyxGOqjMZN1DBI#%7B%22pageId%22%3A%22MYZbLemxwOWpdsTyfFYM%22%7D




