#### Project7

##### VMEmulator
1. (optional) load xxxVME.tst into the VM VMEmulator, run the test script and inspect the program's operation
2. use your translator to translated XXX.vm, the result will be a file name XXX.asm
3. inspect the generated code; if there a problem, fix your translator and go to status 2
4. run the code , inspect the result
5. if there a problem, fix your translator and goto stage 1

#### arithmetic
  eq:

    @sp
    AM=M-1
    D=M
    A=A-1
    D=D-M
    @FALSE
    D;JNE
    @SP
    A=M-1
    M=-1
    @CONTINUE
    0;JMP
    (FALSE)
    @SP
    A=M-1
    M=0
    (CONTINUE)

### PUSH & POP

#### LCL ARG THIS THAT
local argument this that are implemented precisely the same way \
addr = segmentPointer + i, *SP=*addr, SP++  <br/>
addr = segmentPointer + i, SP--, *addr=*SP


#### PUSH
push segment i
* constant:

push constant i => *sp = i, sp++

    @arg
    D=A
    @SP
    A=M
    M=D
    @SP
    M=M+1

* this/that:
* argument:
* local:

addr = LCL + i, *sp=*addr, SP++

    @arg
    D=A
    @LCL
    D=M+D
    A=D
    D=M
    @SP
    A=M
    M=D
    @SP
    M=M+1




* temp:
map to the RAM location 5 to 12
 - push

    addr = 5+i, *SP=*addr, SP++  
 - pop

    addr = 5+i, SP--, *addr=*SP


 * static: \
 the challenge \
 static variables shaould be seen by all the methods in a program
 solution \
 store them in some "gloabl space"
 have the VM translator translate each VM reference static i (in file Foo.vm) into an assembly reference Foo.i \
 Following assembly, the Hack assembler will map these references onto RAM[16], RAM[17],...RAM[256]. \
 Therefore, the entries of the static segment will end up being mapped onto RAM[16], RAM[17], ...,RAM[256] in the order in which they appear in the program \
 push from the static to sp


     @index
     D=M
     @SP
     A=M
     M=D
     @SP
     M=M+1

 * pointer:



#### POP
* constant:
pop constant i => sp--, *sp = i

* argument:
* local:
* temp:
* this/that:

addr = LCL + i, SP--, *addr = *SP

    @LCL
    D=M
    @arg
    D=D+A
    @R13
    M=D
    @SP
    AM=M-1
    D=M
    @R13
    A=M
    M=D

* static:
pop from sp to foo.vm


    @Foo.i
    M=D

    @index
    D=A
    @R13
    M=D
    @SP
    AM=M-1
    D=M
    @R13
    A=M
    M=D


* pointer:

##### win10 虚拟桌面
* win + table
* win + cltr 左右 切换
* win + ctrl D 创建
* win + ctrl F4 删除当前
