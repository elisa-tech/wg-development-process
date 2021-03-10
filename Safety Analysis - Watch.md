Architectural analysis of on an example Linux kernel sub-system
  - In coordination with the Safety Architecture, Automotive and Medical Devices WGs, choose a key Kernel subsystem and work through the “What we can do in ELISA?” proposals        identified in the Testing Process Gap Analysis (.https://docs.google.com/spreadsheets/d/15wbukSZ5lSR-YhzED8ojfFh2FAyAog1o3Hh84-JyRHA/edit#gid=1513725300).
  - It was proposed that the Watchdog sub-component https://linux.die.net/man/8/watchdog is both relevant for current work in the Architecture and Automotive WGs, and also not overly complex, so that the WG could completely work through a number of the proposals. 
  - The Memory Management subsystem was also proposed; this is more complex, but more widely applicable.  It is an option for followup (next task).

1. Owner
      - Elana Copperman (in coordination with Gabriele Paoloni/Safety Architecture WG and Jochen Kall/AUtomotive WG).
 
PROPOSED WORK PLAN - Develop a checklist or skeleton system architecture for the WD subsystem, identifying the APIs, interfaces, and other system configuration features.D:
* Agree on goals and scope; DoD; milestones
* 
* Develop a checklist or skeleton system architecture for the WD subsystem, identifying the APIs, interfaces, and other system configuration features.
* Question - to what level is architecutre/design appropriate for our purpose?
*     - Block diagrams of components + interfaces.  Define on 3 layers (SW; HSI; HW)
*     - Document every single API + parameters - ?
*     - Execution flow - ?
*     - Assumptions (e.g., necessary locks)
*     
* FMEA --> safety goals, failure modes, safety requirements.
* Define safety requirements --> test cases
* Compare existing test frameworks to proposed, identify gaps.
* Anything else?
* 
2. Goals and scope, Architectural analysis of Watchdog subcomponent on 3 levels.  
      - Pure software layer (independent of hardware implementation)
            We should focus our analysis on the pure software layer, focusing on software APIs on a generic hardware emulation.  References:
            
            - https://www.kernel.org/doc/html/latest/watchdog/watchdog-kernel-api.html#  Describes user space interfaces to WT Timer Driver Core Framework (from kernel v5.2)
            - https://github.com/torvalds/linux/blob/master/drivers/watchdog/Kconfig  WD kernel configurations
            - https://github.com/torvalds/linux/blob/master/tools/testing/selftests/watchdog/watchdog-test.c 
            
      - Hardware/Software interface (HSI)
            We should define guidelines for hardware vendors to interface software emulation with their specific hardware.  References:
            
            - https://www.kernel.org/doc/html/latest/watchdog/watchdog-api.html  Most recent version of the basic Linux WD driver API
            - https://cateee.net/lkddb/web-lkddb/WATCHDOG_SYSFS.html  Read WD device status via sysfs attributes
            - https://cateee.net/lkddb/web-lkddb/WATCH_QUEUE.html   Provide a general notification queue for the kernel to pass events to userspace  
            - https://github.com/torvalds/linux/blob/master/drivers/watchdog/watchdog_core.c  WD common core infrastructure
                
      - Hardware implementation
            Up to the hardware vendor, to ensure that the ELISA recommendations are properly implemented on the specific hardware 
            platform.  References
            
            - https://cateee.net/lkddb/web-lkddb/WATCHDOG_RIO.html   Support the hardware watchdog capability on Sun RIO machines (and other similar configs)
            - https://github.com/torvalds/linux/blob/master/drivers/greybus/svc_watchdog.c SVC Greybus WD driver (similar to WD support under other drivers)
            - https://github.com/torvalds/linux/tree/master/drivers/watchdog  HW WD drivers
            
3. Definition of Done
      - An initial draft document summarizing documentation, design, architecture, requirements and test plans (see examples below) for the Watchdog subsystem.  
      - The document should be suitable for sharing with the broader Linux and safety community for feedback and further development.

4. Milestones
      - May 2021 ELISA Workshop - First internal draft for review and discussion
      - October (?) 2021 ELISA Workshop - Second internal draft for review and discussion
      - February (?) 2022 ELISA workshop - Third and final internal draft for review and discussion, opening for public reiew in Feb 2022.
      - April 2022 - Editing and handover, ELISA completion

Some examples:
1. What unit tests, coverage, etc. are available, and what requirements do they satisfy?
      - Linux Kernel tests are part of the kernel code base, and there are defined selftests for the Watchdog subsystem. Task to investigate the defined Watchdog selftests and 	         evaluate coverage and relevance for compliance with safety standards.  See https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/dev-tools
      - Find and include external tests that might be relevant to the WD subsystem.
      - Find and include kernel configurations that might be relevant to the WD subsystem in use on the product.

2. Identify and formalize a set of requirements for the WD component and use this to derive test cases to check these requirements. Purpose is to have a set of requirements- based tests able to run together with other existing syscall tests (fuzzers, etc.).
      - Define a suitable combination of methods to derive test cases (requirements analysis, equivalence classes, boundary values, error guessing). In addition to unit tests and other defined tests, define goals to identify gaps. We should determine if we can suggest more tests, or improve current tests.
      - Document requirements on kernel-based functionality.
      - Consider formal methods for generation of test cases (e.g., Daniel B.’s work on RT formal verification).

3. Develop a checklist or skeleton system architecture for the WD subsystem, identifying the APIs, interfaces, and other system configuration features.
      - Use callgraph or other relevant tools.
  ** Begin with this point, based on references, in conjunction with (5) below.  Identify potential failure modes 
 
4. Software integration and verification. Identify and formalize a set of requirements for the WD component and use this to derive test cases to check these requirements. Purpose is to have a set of requirements-based testing able to run together with other existing syscall tests (fuzzers, etc.).
      - Define a suitable combination of methods to derive test cases (based on requirements, equivalence classes, boundary values, error guessing). 	 	
      - Document requirements in kernel, based on functionality.

5. “Reverse engineer” architectural-level requirements from existing tests and/or information in patch discussions, using WD component. 	
      - Requirements coverage by test cases on the software architectural level should be determined in order to demonstrate completeness. Incompletely covered requirements may          be supplemented with additional test cases or by other relevant means.
      - Decide if and how to publish the results of the WD testing analysis. Ideally as part of the code base, and to correlate with existing tests to support traceability.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

See Watchdog_architecture document for a high level block diagram of a simple Watchdog architecture.

See Watchdog_diagram document for a high level summary of the 3 levels (sw/hsi/hw).

See https://github.com/torvalds/linux/blob/master/tools/testing/selftests/watchdog/watchdog-test.c - basic selftexts.
What is included?  Test of basic WD functionality:  Watchdog device is found and successfully opened.  In addition, the following information can be derived:
1. BootStatus - If last boot was caused by watchdog or power-on-reset.
2. Disable - If watchdog card is disabled.
3. Enable - If watchdog card is enabled.
4. Ping rate - number seconds to which watchdog ping rate is set.
5. SetTimeout - Sets watchdog timeout to given number of seconds.
6. Gettimeout - Returns number seconds to which watchdog timeout rate is set.
7. SetPretimeout - Sets watchdog pretimeout (for multiple stage WD) to given number of seconds 
8. Getpretimeout - Returns number seconds to which pretimout rate is set.
9. Gettimeleft - Returns number seconds left to next timeout.
10. Info - Returns watchdog info (identity, firmware version, supported options).
