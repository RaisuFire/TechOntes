## Python GIL global interpreter lock

** 并发 并行**

不管你多少个线程，只要你系统能处理多个事情，就是并发的
并行 这些事情都是在同一时间执行的 多线程 多进程

** 同步异步 **

事件发生与否，需要你自己去检查
事件的发 生与否，这个是别人通知给你的
阻塞非阻塞



** 编译 解释 JIT **

编译？ 一个代码编译成另外一种代码，编译到机器码，目标代码就是机器码 <br>
解释？ c语言是统一的，那我用c语言写出一个虚拟机，这个机器是可以部署到任何机器的 <br>
python语言，语言逐条转换成对应的虚拟机指令 <br>
JIT just in time compiler 把最热的代码替换成编译到机器码

** 动态VS静态 **
    a = ''
    a = 1
    a = True

    a = ''
    a = 'hello'
    a = 'test'

** 强类型弱类型 **

    1 + '1'
    1 + 1

有GC 无GC garbage collection <br>

new delete // malloc free c, c++
有gc: java golang python ruby scala js
new
1. mark & sweep concurrent mark sweep
2. ref counting

python
    1. ref counting
    2. mark & sweep

    a b
    a.parent = b
    b.child = a

    weakref
