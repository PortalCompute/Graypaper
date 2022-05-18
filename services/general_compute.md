---
layout: default
title: Generalized Compute Oracle Networks
nav_order: 1
parent: Services
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
permalink: /technology/services/general_compute
grand_parent: Technology
---
# Generalized Portal Compute Oracle Network (G-PCON)
> *Portal Nodes* are only capable of running the functions in their *Portal Compute Base*. From a software development point of view, it is tedious for developers to implement new functions in the *PCB* each time they desire new functionality from a *PCON*. From a security point of view, each edit to the *PCB* will require a security audit which can be cost-prohibitive.

> To get around this, a single function in the *PCB* can invoke the execution of a general-purpose runtime. We refer to this type of oracle network as a *G-PCON*. In this case, all implementation details of a *G-PCON* can be abstracted away from the end-user. A user is only required to submit a program/binary to the *G-PCON* to be executed on their behalf.


## Runtimes
> There are a variety of generic runtimes that the *G-PCON* can execute, each with its own set of tradeoffs. Below are target runtimes that capture a sufficient number of use-cases. 

> ### WASM Interpreter
>> Compiled languages (i.e. Rust, C++, C, etc) and even subsets of JavaScript can compile programs down to WebAssembly binaries. A WASM interpreter executes the instructions in the binary, updating the state of a virtual machine. *G-PCONs* implementing a WASM interpreter can execute arbitrary WASM binaries with provably correct results. 

> ### RISC-V Emulator
>> Similar to the WASM interpreter, a RISC-V emulator allows for executing arbitrary RISC-V binaries. A *G-PCON* can implement an open-source RISC-V processor in software and then emulate the execution of arbitrary RISC-V binaries.  

> ### EVM Emulator
>> By implementing an EVM emulator, a *G-PCON* can execute arbitrary Solidity bytecode. This runtime allows smart contract developers to offload compute-intensive Solidity functions to the *G-PCON* without requiring knowledge of other programming languages or build systems.

> ### Python Interpreter
>> A Python-savvy smart contract developer can submit entire Python programs/functions to the *G-PCON* to execute off-chain.  

> In all cases, since everything in the *G-PCON* remains private, even the input program/binary can remain fully encrypted and thus private from the blockchain. The *G-PCON* can prove that the results (encrypted or not) came from an encrypted input program, which enables new use-cases like the use of proprietary algorithms on public blockchains.

> Below is describes the overall workflow of a *G-PCON*, but implemented with a WASM interpreter. Substituting a different runtime will look identical. 
![G-PCON](../../gifs/general_compute.gif)

