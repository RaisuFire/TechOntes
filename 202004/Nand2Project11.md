#### Compiler development readmap
* finaly finish the compiler!!!
* methodolgy: extending the basic syntax analyzer and adding code generation capabilities
* compilation  
    1. each class is compiled separately  


##### symbol tables
* class-level symbol table:   
can be reset each time we start compiling a new class
* Subroutine-level symbol table  
can be reset each time we start compiling a new subrountine
* add the variable and its properites to the symbol table
* look up the variable in the subroutine-level symbol table; if not found, look it up in the class-level symbol table, not , return a error msg
* nested scoping
    - some languages feature unlimited nested scoping
    - can be managed using a linked list of suymbol tables(start in the first table, if not found, lookup the next table, and so on)

##### Handling Expressions
* translate from infix to postfix
* generating code for expressions:
    1. a one-stage approach
* from parsing to code generation

##### Handling Flow of Control
* the flow of control vm code using:
        goto

        if-goto

        label
* A program typically contains multiple if and while statements  
solution: the compiler can ensure that the generated labels are unique
* The if and while statements are often nested.  
Solution: the compiler employs a recursive compilation stategy


##### Handling Objects
* Low-Level Aspects
    - Object data is accessed via the this segment
    - Array data is accessed via the that segment
    - Before we use these segment, we must first anchor them using pointer

* Object construction
        var Point p1, p2;
        var int d;
        ...
        let p1 = Point.new(2, 3);
        let p2 = Point.new(5, 7);
        ...
    - During compile-time:  
    the compiler maps p1 on local0, p2 on local1, d on local2
    - During run-time, the execution of the constructor's code effects the creation of the Objects themselves, on the heap

* manipulation
    - compiling method calls: the general technique
            obj.foo(x1, x2)

            push Obj
            push x1
            push x2
            push...
            call foo
    - compiling void methods
            push constant 0
            return

            do p1.print()

            ...
            push p1
            call Point.print
            // the caller of a void method
            // must dump the return value
            pop temp 0

##### Handling Arrays
* RAM access using that
        // RAM[8056] = 17
        push 8056
        pop pointer 1
        push 17
        pop that 0
    - pop pointer 1
    the VM implementation ...
        * sets THAT = stack.pop()
        * aligns that 0 with the RAM address whose value is THAT
    - pop that 0
        * sets that 0 = stack.pop()
        * sets the RAM address aligned with that 0 to the same value

* Array access
        // arr[2] = 17
        push arr
        push 2
        add
        pop pointer 1
        ppush 17
        pop that 0
