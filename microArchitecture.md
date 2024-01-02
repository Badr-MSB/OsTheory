# CPU Structure

Inside the CPU, an instruction pass trought the five following stages : 

--> Fetch instruction (FI) \
--> Decode instruction (DI) \
--> execute instruction (EXEC) \
--> Store mem value (MEM) \
--> write Back (WB)

# FrontEnd
FI/DI form the frontend level of the CPU. Their role is to provide as many as possible decoded instruction from instruction memory.

## Fetch

the fetch of istructions is the process of copying instructions from memory into the CPU. the main problem faced at this stage is which instruction to choose in case we have a conditionnal branchement. lets analyse the following example :


I1 : int i = 0 ;\
I2 : i++; \
I3 : if (i > 1){ \
I4 : i++; } \
I5 : i = i * 2;

The question here is : What instruction should we fetch after I3 ? I4 or I5 or wait until the I3 to be executed ?

If we decide to wait for the execution of I3 and then decide, it will be a lose of eneregy.
This is what it should be better to try to predict the branchement (I3).

### Branchs Prediction 

The simplest prediction that we can use, is the **1-bit Counter Predicter**. This predicter take 0 or 1 as value , if the prediction is correct he conserve its state, else he change it.

