### Project8
##### Branching Command
* goto label \
  jump to execute the command just after label
* if-goto label \
  cond = pop;
  if cond jump
* label label \
  label decalaration command


##### Function
* define

High-level  | Pseudo VM code | Final VM code
----------- | -------------- | -------------
int mult (int x, int y) {} | function mult(x, y) | function mult 2

* executing
  - call method argNums
    1. pass parameters from the calling function to the called function
    2. Detemine the return address within the caller's
    3. save the caller's return address, stack and memory segments
    4. Jump to execute the called function

* return \
  take the executed value and puts it on the stack of caller instaead of the arguments that were pushed previously \
  must push a value onto the stack

    1. return to the caller the value computed by the called function
    2. recycle the memory resources used by the called function
    3. reinstate the caller's stack and memory segments
    4. jump to the return address in the caller's code


#### Implement
##### call
calls the function, informing that nArgs arguments have been push onto the stack


    push returnAddress
    push LCL
    push ARG
    push THIS
    push THAT
    ARG = SP - 5 - nArgs
    LCL = SP
    goto functionName
    returnAddress

#####  function
here starts a function that has nVars local variables

    (functionName)
    repeat nVars times;
    push 0;
    ...
##### return

    endFrame = LCL
    retAddr = *(endFrame - 5)
    *ARG = pop()
    SP = ARG + 1
    THAT = *(endFrame - 1)
    THIS = *(endFrame - 2)
    ARG = *(endFrame - 3)
    LCL = *(endFrame - 4)
    goto retAddr
