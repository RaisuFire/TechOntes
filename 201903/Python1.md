
1. generator
2. iterator
3. class method, instance method, static method
4. lambda closure
5. *args **kwargs
6. magic method
7. list comprehension
8. dict comprehension
9. decorator
10. 默认参数

***

##### generator


在Python2里面：


    for i in range(1000000000)
    for i in xrange(100000000)

    l = [1...1000000000]
    for i in l:
        print(i)

希望1就够了

    def my_range(n):
        i = 0
        while i != n:
            i += 1
            yield i


    r = my_range(10)
    for i in r:
        print(i)

##### iterator

for ?

    for (int i = 0; i < i_max ; i ++)
    i = 0 i= 1初始化赋值
    i++ 递进 i= i + 2

    1. iter iter(obj) obj.__iter__()
    2. next next(obj) obj.__next__()

(a)

    for i in range(10):
        pass

(b)

    iter_obj = range(10)
    iter(iter_obj)

    while True:
        try:
            i = next(iter_obj)
        except StopIteration:
            break
<br>

    class Pow2(object):
    def __init__(self, max):
        self.max = max
        self.n = 0

    def __iter__(self):
        self.n = 0
        return self

    def __next__(self):
        if self.n < self.max:
            self.n += 1
            return 2 ** self.n
        else:
            raise StopIteration


    p = Pow2(10)
     for i in p:
         print(i)


##### class method, instance method, static method

    class A(object):
        @staticmethod
        def s_foo():
            pass

        @classmethod
        def c_foo(cls):
            pass

        def foo(self):
            pass

    a = A()
    a.foo()
    A.c_foo()



##### 引用类型
[] {}

深拷贝 浅拷贝

    from copy import deepcopy
    l1 = []
    l2 = deepcopy(l1)
    l1.append(1)
    print(l2)

    l1 = [1, [1, 2], 3]
    l2 = l1[:]

    def foo(a=[]):
        a.append(1)
        print(a)

    foo()
    foo()

# lambda closure closure ref

1. algorithm sort(lambda x : x['key'])
2. map reduce filter


    def greeting(msg):
        def hello(name):
            print(msg, name)
        return hello

    h = greeting("welcome")
    h("akira")

    l = []
    for i in range(10):
    def _(i=i):
        print(i)
        l.append(_)
    for f in l:
        f()


##### args kwargs
tuple  <br>
dict <br>
*args  a,b,c,d <br>
**kwargs k = v <br>
****
##### list comprehension  列表推导
。。。

##### decorator
AOP aspect oriential programming

    def simple_wrapper(fn):
        def _():
            #print(fn.__name__)
            return fn()
        return _

    def fix_arg_wrapper(fn):
        def _(x):
            #print(fn.__name__)
            return fn(x)
        return _

    def all_args_wrapper(fn):
        def _(*args, **kwargs):
            print(*args, **kwargs)
            return fn(*args, **kwargs)
        return _

    @simple_wrapper
    def foo():
    pass

    @all_args_wrapper
    def bar(a, b, c):
    pass

    #foo()
    bar(1, 2, 3)

##### magic method

    class LogAll(object):
        def __init__(self):
            self.a = 1
            self.b = 2
            self.c = 3
        def __getattribute__(self, item):
            print(item)

    l = LogAll()
    print(l.a)
    l.a = 1
    l.b
    l.c

    class Any(object):
        def __getattr__(self, item):
            print(item)

        def __setattr__(self, key, value):
            print("set", key, value)

    a = Any()
    a.a
    a.a = 1

    class Any(object):
        def __getattr__(self, item):
            def _(*args, **kwargs):
                print("function name", item)
                print("args", args)
                print("kwargs", kwargs)

            setattr(self, item, _)

            return _


    a = Any()
    a.fuck(1, 2, 3)
    a.shit(1, 2, [1, 2, 3], c=[])



##### mixin
C, C++, Java

    b -> a
    a -> b

    a -> a interface
    b -> b interface

    b->a interface
    a->b interface

Python

    Final(A,B,C)

<br>

    class A(object):
        def foo(self):
            print("foo")
        def bar(self):
            print("bar")
            self.shit()

    class B(object):
        def shit(self):
            print("shit")

    class C(A, B):
        pass

    c = C()
    c.bar()
