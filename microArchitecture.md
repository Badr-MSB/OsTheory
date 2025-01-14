# Architecture & MicroArchitecture
An architecture (x86_64,ARMv8,RISC-V) is the specification of the architectural state (wich is manipulated by the software registre, mémoire ...) and how it can change (instructions, exceptions ...) 

the instruction architecture is called ISA

A microarchitecture (Zen,A72,Boom) is the hardware that implements the architecture in an independent manner from the software. the microarchitacture contains the folowing concepts :
- pipline
- in-order and out of order execution
- memory access scheduling policy 
- speculative execution
- superscalar processing
- clock gating
- caching
- prefetching
- 

# CPU Structure

Inside the CPU, an instruction pass trought the five following stages : 

--> Fetch instruction (FI) \
--> Decode instruction (DI) \
--> execute instruction (EXEC) \
--> Store mem value (MEM) \
--> write Back in a register (WB)

Many optimisations are introduced in current CPUs, for example :
- In order to increase clock fréquancy CPUs are designed to operate each stage in an one-cycle operation to permit a piplined execution. 
- CPUs adopte the speculation execution to minimize the time wasted on waiting for branchement  
- Superscalar execution : multiplying hardware capabilities in order to execute a given stage for many instructions.
- Out-of-order execution

# FrontEnd
FI/DI form the frontend level of the CPU. Their role is to provide as many as possible decoded instruction from instruction memory.

## Fetch

the fetch of instructions is the process of copying instructions from memory into the CPU. 
### Specular execution
the main problem faced at this stage is which instruction to choose in case we have a conditionnal branchement. lets analyse the following example :


I1 : int i = 0 ;\
I2 : i++; \
I3 : if (i > 1){ \
I4 : i++; } \
I5 : i = i * 2;

The question here is : What instruction should we fetch after I3 ? I4 or I5 or wait until the I3 to be executed ?

If we decide to wait for the execution of I3 and then decide, it will be a lose of eneregy.
This is what it should be better to try to predict the branchement (I3). This solution is called **Specular execution**

### Specular execution : Branchs Prediction 

The simplest prediction that we can use, is the **1-bit Counter Predicter**. This predicter take 0 or 1 as value , if the prediction is correct he conserve its state, else he change it.

for this serie of prediction it may works, (if we consider that the counter begin with 1) :

| Prediction | real evaluation of the branch|
| 1 1 1 1 ...|  1 1 1 1 ...                 |

but for this the failure is 100% : 

| Prediction | real evaluation of the branch|
| 1 0 1 0 ...|  0 1 0 1 ...                 |

A 2-bits counter improve prediction compairing to the 1-bit one because the first one needs 2 mistakes ,as maximum, to change its decission. However, it stills a blind manner to predict, if you analyse this n-bit counter méthodes you will feel that the prediction is not smart enough.

## BackEnd

### Pipline

The pipline is a way of executing instructions without waiting the end of its execution to grub another one. In this method all stages are computing their results.
### Pipline : Problem 

Structural dependencies :
Architectural dependencies : 
- Data dependecies : is the consumer / productor dependency
- Controle dependencies : banchement dependency
### Solution
solution : bypass network
