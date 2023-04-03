# OpenHW Project: corev-llvm-project Plan Approved CV32E40P-V2

| Gate                                 | Status                                                     |
| ------------------------------------ | ---------------------------------------------------------- |
| PC gate: Project Concept             | Approved on 2020-11-21 as Preliminary Project Launch (PPL) |
| PL gate: Project Launch              | Approved on 2022-xx-x                                     |
| PA gate: Plan Approved               | Presented on 2022-11-28 for **2023 workplan**, approved on 2023-xx-xx |
| PA gate: Plan Approved               | 2024 and beyond workplan in future PA gate |

Author: ChunyuLiao

## Summary of project

This document should be read in the context of the overall CORE-V LLVM project project launch proposal.  It does not duplicate information from that document.

This plan is to deliver Clang/LLVM compiler support for all of the CV32E40P version 2 instruction set extensions.

### Summary of Timeline

CORE-V LLVM project is a long-run project. It is therefore difficult to plan the complete project.

Therefore, in order to keep the project under control, the project plan is defined for 2023 activity.

During 2023 we plan to support all ISA extensions in the assembler (H1/2023) and all ISA extensions through builtins in the compiler H2/2023). A detailed timeline is provided in this document. 

## OpenHW Members/Participants committed to participate in CORE-V LLVM project

- Embecosm 
- Institute of Software Chinese Academy of Sciences (ISCAS/PLCT)

## Project Leader(s)

- Charlie Keaney (overall LLVM project lead)
- Chunyu Liao (project lead for the project to support LLVM on the CV32E40Pv2 processor)

## Project Planning Documents

The progress towards the milestones will be tracked during progress meetings, usually every week.

A monthly report will be provided to the Software Task Group.

## Summary of requirements

### CORE-V LLVM project features

After approval by the TWG, it will be managed in OpenHW GitHub.

As a summary, contains:

+ Clang/LLVM tool chain for C and C++:
    + assembler
    + compiler
    + support for ISA extensions

+ The components being supported
    + support CV32E40Pv2 target
    + support 32-bit CORE-V target
    + support ISA extension
        + xcvhwlp (hardware loops)
        + xcvmac (multiply-accumulate)
        + xcvbi (immediate branch)
        + xcvmem (post-indexed and register-indexed memory access)
        + xcvalu (miscellaneous ALU operations)
        + xcvsimd (PULP 8/16-bit SIMD)
        + xcvbitmanip (PULP bit manipulation)
        + xcvelw (event load word) 

The project will use the existing GNU linker and debugger. The standard RISC-V newlib and compilerRT libraries will be used unchanged. The newlib library will be used on bare metal.

### License scheme

The LLVM project mostly uses Apache licensing. The full details of all licenses is addressed in the Project Launch document.

### Verification

Github Continuous Integration and Test (CI) will be set up. Initial support for CI: https://github.com/openhwgroup/corev-llvm-project/pull/23

## Explanation of why OpenHW should do this project

This document should be read in the context of the overall CORE-V LLVM project project launch proposal.  It does not duplicate information from that document.

## Industry landscape: description of competing, alternative, or related efforts in the industry
This document should be read in the context of the overall CORE-V LLVM project project launch proposal.  It does not duplicate information from that document.

### Market differentiators
## External dependencies
+ Prequisites:
    + a suitable platform for regression testing the compiler.
       * expected to be either OVPSim or the Verilator model of CV32E40Pv2 due in early 2023.
    + agreement on the instruction set encodings to be compliant with the RISC-V standard.
       * draft is currently in [this spreadsheet](https://github.com/openhwgroup/cv32e40p/files/9949531/pulp_encoding_blocks-OPHW-2022-10-07.xlsx).
+ External dependencies:
    + ongoing tracking of upstream LLVM development until the CORE-V tool chain is accepted upstream. eg: rebase upstream code
    + OVPSim licenses from Imperas if this is chosen for regression testing.

## List of project outputs
+ Final deliverables
    + extensions to upstream LLVM compiler tools to support CORE-V in the upstream llvm-project repository;
    + revisions to the CORE-V design specifications to clarify ambiguities.

+ Interim deliverables
    + The Corev-llvm-project meets every week;
    + Reports on progress to the monthly SW TG, Slides will be updated during the meeting and posted on LLVM Tools and Kanban Board Mattermost channels;
    + progress against work packages;
    + regression test results;
    + updates to the project plan; and
    + extensions to upstream LLVM compiler tools to support CORE-V in the OpenHW Group llvm-project repository development branch.

+ Continuously updated source code as new features are added.


### Documentation:
This will follow the upstream project structure.

### Design
This will follow the upstream project structure.
 
### Verification:
This will follow the upsream project structure. In addition the project will use a subset of the GCC regression tests to verify execution behavior.

### OpenHW engineering staff resource plan: requirement and availability

### Engineering resource supplied by members - requirement and availability

1 Senior engineer from PLCT 

### Marketing resource - requirement and availability
### Funding for project aspects - requirement and availability
This project is funded by PLCT

## Architecture and/or context diagrams
This can be found in the upstream project

## Who would make use of OpenHW output

Everyone who wants to develop software for CORE-V family of cores and devices implementing the CORE-V extensions will need a compiler.  They have a choice to use the CORE-V GCC compiler tool chain or the CORE-V Clang/LLVM tool chain (this project).


## Project license model

See License Scheme above.

## Description of initial code contribution, if required

embecosm - V1
The embecosm contribution is already [in the repo](https://github.com/openhwgroup/corev-llvm-project/commits/development), from [e96fda8](https://github.com/openhwgroup/corev-llvm-project/commit/e96fda82f1e93050f413ed1c13640c93dfb80921) to [6c12852](https://github.com/openhwgroup/corev-llvm-project/commit/6c128521db382f74eaf78b5268e6256606c564ff). This contains support for some of the directives, but they may not apply to CV32E40PV2 and will need to be modified.

## Repository Structure

The full code will initially be stored in the following github repository:
https://github.com/openhwgroup/corev-llvm-project/tree/development

The upstream code which is the eventual target for this project is in the following repository:
https://github.com/llvm/llvm-project

## Project distribution model

See the Project Launch document for details.

## Project plan

### 2023 workplan

All instructions for the final CV32E40PV2 should be identified in [this issue](https://github.com/openhwgroup/cv32e40p/issues/452). Currently it is following [this spreadsheet](https://github.com/openhwgroup/cv32e40p/files/9949531/pulp_encoding_blocks-OPHW-2022-10-07.xlsx) to implement.

[This document](https://github.com/openhwgroup/cv32e40p/blob/master/docs/source/instruction_set_extensions.rst) can be consulted, but it does not prevail.

CORE-V builtin names in [this doc](https://github.com/openhwgroup/core-v-sw/blob/master/specifications/corev-builtin-spec.md)

| Related TG         | Milestone                                                                                                                      | Target        | Contributor |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------ | ------------- | ----------- |
| Assembler          | re-encode the existing CV32E40Pv1 instructions(alu, hwlp, mac, mem already have the first version, if the code is not consistent, re-encoding to make it suitable for CV32E40P)                                                                                 | 2023-02-28    | ISCAS       |
| Assembler          | SIMD instructions(According to the above document, SIMD ALU Encoding, SIMD Comparison Encoding and SIMD Complex-numbers Encoding should be included)                                                                                                              | 2023-03-30    | ISCAS       |
| Assembler          | Bit Manipulation Encoding, Event Load Instructions, etc. This time should contain all assembly instructions.                       | 2023-04-30    | ISCAS       |
| Compiler options   | CV32E40Pv2 has its own compilation options, support it. (xcvhwlp,xcvsimd,xcvbi,xcvmem,xcvalu,xcvmac,xcvbitmanip,xcvelw )                                                 | 2023-05-30    | ISCAS       |
| Codegen            | SIMD builtins(Please see corev-builtin-spec.md for more details)                                                               | 2023-07-30    | ISCAS       |
| Codegen            | Bitmanip builtins(Please see corev-builtin-spec.md for more details)                                                           | 2023-09-30    | ISCAS       |
| Codegen            | ALU builtins(Please see corev-builtin-spec.md for more details)                                                                | 2023-10-30    | ISCAS       |
| Codegen            | Post-indexed and register-indexed memory access builtins. This time should contain all builtins.                               | 2023-11-30    | ISCAS       |
| Hardware loop      | CV32E40Pv1 has already implemented version 1, and new features will be added to it later                                       | 2023-12-30    | ISCAS       |

### Risk register

|                           | Likelihood (1-10) | Impact (1-3) | Overall |  Avoidance&nbsp;/ Mitigation                                                   |
| ------------------------- | :---------------: | :----------: | :-----: | --------------------------------------------------------------------------- |
| Not enough resources      | 8                 | 3            | 24      | More technical participants are welcome. Prioritize most important features first.                                       |
| Insufficient coordination | 5                 | 2            | 10      | Weekly meetings                                                               |
| Conflicting contributions | 5                 | 2            | 10      | Weekly meetings                                                               |
