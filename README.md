# CS255-System-Analysis-and-Design

Project Summary

The DriverPass project was completed for a fictional client named Liam, the owner of a startup called DriverPass. Liam identified a gap in the market: too many people were failing their driving tests at the DMV, and there was no structured way for them to prepare. He hired our consulting team to design a web-based system giving students access to online practice tests, training packages, and a way to schedule on-the-road driving lessons with certified instructors. The system also needed to support office staff who book appointments on behalf of customers, an IT officer who manages accounts and access, and the owner who generates and downloads activity reports. A key requirement was a live connection to the DMV so that practice test content updates automatically when regulations change. The deliverables included a business requirements document, UML use case, activity, sequence, and class diagrams, a technical requirements document, and a client-facing presentation.


Reflection

What did you do particularly well?

The area where I feel strongest is the thoroughness of requirements gathering and how faithfully it translated into the UML diagrams. Rather than designing a generic system and labeling it DriverPass, I stayed close to the interview transcript at every step. Details that could have been easy to overlook found their way into the diagrams in concrete ways: the secretary as a distinct actor who books on behalf of customers, the requirement that every reservation be logged with the name of the person who made it, the four specific test status values Liam described, and the fact that the system must track which driver and car is paired with each student. The class diagram reflects that discipline clearly. The Student class carries the exact registration fields Liam listed, the Lesson class has bookedBy and lastModifiedBy attributes, the Package class has a status field for active versus disabled, and the Car class exists because Liam mentioned it explicitly.

If you could revise one part of this work, what would you pick and how would you improve it?

I would revise the activity diagrams. The scheduling diagram captures the two booking paths and the audit logging step, but it does not model the modification and cancellation flow in any detail. In a more complete version, I would add a branch handling what happens when a student wants to change or cancel a reservation, including how the system updates driver and car availability and logs the change with the same accountability fields as the original booking. Liam specifically said he needs to know who canceled an appointment, not just who made one, and a more thorough diagram would model that path explicitly.

How did you interpret the user's needs and implement them into your system design?

My approach was to treat the interview transcript as the authoritative source and build upward from there rather than designing a system first and checking it against requirements afterward. Every use case maps to something a specific person in the interview said they needed to do. Every class attribute traces to a field or data point that came up in conversation. When Liam said he needed to know who made, canceled, and modified each reservation, that became two explicit attributes on the Lesson class and a dedicated Audit Log Service in the sequence diagram. When Ian said the team does not want to deal with backup and security, that steered the technical requirements toward managed cloud hosting rather than on-premise servers.

Considering user needs matters because a system that is technically well-built but misaligned with actual workflows is not a successful system. If the design only allows students to book their own appointments, the secretary cannot do her job. If reports can only be viewed on screen, Liam cannot take them home to work in Excel. Getting those details right is not decoration; it is the actual job.

How do you approach designing software, and what techniques or strategies would you use in the future?

My approach moves from broad to specific: understand the problem fully before committing to any structural decisions. In this project that meant spending significant time with the interview transcript before drawing a single diagram, identifying all actors and what each one genuinely needs, and separating functional from nonfunctional requirements so that both the what and the how-well are covered. From there, the UML diagrams form a natural progression. Use case diagrams establish scope, activity diagrams trace how processes flow, sequence diagrams show how objects communicate, and class diagrams define the data model that supports everything else.

Going forward, I would add a traceability matrix mapping each requirement to the diagram element or class attribute that addresses it. That kind of artifact makes gaps easier to catch early and makes it simpler to verify that nothing was lost between requirements gathering and implementation. I would also invest more time in alternative flows during activity diagramming, since those are the scenarios most likely to surface during testing and most likely to have been underspecified up front.
