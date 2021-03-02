# wg-development-process
The Kernel Development Process WG will be working on a predefined list of tasks agreed by the group.  
The task list will be updated from time to time, as tsaks are completed or rejected, when relevant.
The initial task list agreed by the WG is outlined below.
For each task there is a dedicated owner.  Owner responsibilities include:
   - Initial scoping 
   - Track status and provide leadership
   - Handover / park the task if they can no longer spare the time to own

For each task we define:
  - Goals and scope of the topic
  - "Definition of Done" for that task - e.g., create a skeleton of the document for review with one section fully populated.
  - Milestones

1. Safety analysis of on an example Linux kernel sub-system
  - In coordination with the Safety Architecture, Automotive and Medical Devices WGs, choose a key Kernel subsystem and work through the “What we can do in ELISA?” proposals        identified in the Testing Process Assessment.
  - It was proposed that the Watchdog sub-component is both relevant for current work in the Architecture and Automotive WGs, and also not overly complex, so that the WG            could completely work through a number of the proposals. 
  - The Memory Management subsystem was also proposed; this is more complex, but more widely applicable.

2. "Big picture" for Tools subgroup.  
   - Owner: Lukas Bulwahn
   - Engage with the Tools subgroup to define the “big picture” for their work on static analysis and MISRA checkers.
   – Analyze how the results for specific examples can be built up to a methodology which justifies why a patchset for a new feature should be added:
        - Compliance with requirements 	
        - Compliance between source code and specs (is this relevant for Linux? Where are the specs?)  	
        - Compliance with HSI spec (see intro to WD analysis above, we need to define such a spec for Linux so that we can analyze the hardware software interface). 	
        - Absence of unintended functionality 	
        - Implementation of safety measures derived from the safety analysis.
