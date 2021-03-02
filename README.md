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
   - Owner: Elana Copperman
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

3. Code coverage, generalize results from Eli Gurvitz's mentorship project.
   - Owner: Eli Gurvitz
   - Look at adding tests to improve coverage. Derive a methodology / set of guidelines to assemble the pieces and infrastructure available to formulate MC/DC level testing. 
   - We may need a combination of tools and a way to demonstrate at the end that we have full coverage.
   - Engage with Eli G. and perhaps coordinate a follow up mentorship project.
   
4. Kernel configurations
   - Owner: Elana Copperman
   - Continued low key (mostly offline) work on kernel configuration database.
   - Elana to work offline, based on workshop 	feedback. Present to WG for feedback and alignment in ~6 weeks (tentatively on April 22) and plan an extended (~1 hour) session at the next workshop. 	
   - Identify safety kernel configurations which can be defined for specific use cases. 
Stretch goal, pending preliminary results from work on safe kernel configuration database.

5. Improve documentation
   - Owner: Paul Albertella
   - Improve documentation of APIs in Linux kernel, as well as documentation of kernel interfaces (to user, hardware, between components) and behavior.
   - Following model of (1) above, start with a specific agreed area to focus. 	
   - Following model of (4) above, work offline and periodically align with the WG. 	

6. Publish results
   - Owner: Paul Albertella.
   - Finalize and publish report on test frameworks; needs review and editing. Details TBD following next TSC meeting and clarifications from Kate (+ consensus with TSC). How,        when to publish; pitfalls to avoid.
   - Publish the Reference Process, to provide information on safety standard expectations for those who do not have access to the safety standards documents. Issue to resolve:          does the Reference Process infringe the copyright for the source standards that it indexes / references?

7. Further process assessment
   - Owner: Peter Brink.  Contributors: Kent Nelson (co-owner), Kate Stewart (existing document from Jochen), Roberto Paccapeli (ERP)
   - Extend the analysis applied to the Testing Process Assessment to cover other aspects of the Reference Process / standards. e.g. Tasks related to section 8 of ISO26262            (from line 48 in the testing process assessment spreadsheet).
   - Revisit and see if there is anything relevant for follow up.
   - How do we extend to other (no-automotive) standards?
