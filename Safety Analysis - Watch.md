Safety analysis of on an example Linux kernel sub-system
  - In coordination with the Safety Architecture, Automotive and Medical Devices WGs, choose a key Kernel subsystem and work through the “What we can do in ELISA?” proposals        identified in the Testing Process Assessment.
  - It was proposed that the Watchdog sub-component is both relevant for current work in the Architecture and Automotive WGs, and also not overly complex, so that the WG            could completely work through a number of the proposals. 
  - The Memory Management subsystem was also proposed; this is more complex, but more widely applicable.

1. Owner
      - Elana Copperman (in coordination with Gabriele Paoloni/Safety Architecture WG and Jochen Kall/AUtomotive WG).

2. Goals and scope, Analysis of Watchdog subcomponent on 3 levels
      - Pure software layer (independent of hardware implementation)
            We should focus our analysis on the pure software layer, focusing on software APIs on a generic hardware emulation
      - Hardware/Software interface (HSI)
            We should define guidelines for hardware vendors to interface software emulation with their specific hardware
      - Hardware implementation
            Up to the hardware vendor, to ensure that the ELISA recommendations are properly implemented on the specific hardware 
            platform
            
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
      - Linux Kernel tests are part of the kernel code base, and there are defined selftests for the Watchdog subsystem. Task to investigate the defined Watchdog selftests and 	         evaluate coverage and relevance for compliance with safety standards.
      - Find and include external tests that might be relevant to the WD subsystem.
      - Find and include kernel configurations that might be relevant to the WD subsystem in use on the product.

2. Identify and formalize a set of requirements for the WD component and use this to derive test cases to check these requirements. Purpose is to have a set of requirements- based tests able to run together with other existing syscall tests (fuzzers, etc.).
      - See Table 8, as well as Annex QR, define a suitable combination of methods to derive test cases (requirements analysis, equivalence classes, boundary values, error              guessing). In addition to unit tests and other defined tests, define goals to identify gaps. We should determine if we can suggest more tests, or improve current                tests.
      - Document requirements on kernel-based functionality.
      - Consider formal methods for generation of test cases (e.g., Daniel B.’s work on RT formal verification).

3. Develop a checklist or skeleton system architecture for the WD subsystem, identifying the APIs, interfaces, and other system configuration features.
      - Use callgraph or other relevant tools.

4. Software integration and verification. Identify and formalize a set of requirements for the WD component and use this to derive test cases to check these requirements. Purpose is to have a set of requirements-based testing able to run together with other existing syscall tests (fuzzers, etc.).
      - See Table 11, define a suitable combination of methods to derive test cases (based on requirements, equivalence classes, boundary values, error guessing). 	 	
      - Document requirements in kernel, based on functionality.

5. “Reverse engineer” architectural-level requirements from existing tests and/or information in patch discussions, using WD component. 	
      - Requirements coverage by test cases on the software architectural level should be determined in order to demonstrate completeness. Incompletely covered requirements may          be supplemented with additional test cases or by other relevant means.
      - Decide if and how to publish the results of the WD testing analysis. Ideally as part of the code base, and to correlate with existing tests to support traceability.