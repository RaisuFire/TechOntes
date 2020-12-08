#### 对象的组合


#### 部署Java应用程序
* jar
* java web start
* 服务加载器   

#### JavaCore 并发
* 线程属性

  * 未捕获异常处理器
* 同步

  * 条件对象


      newCondition()
      await()
      signalAll()
      signal()

  * synchronized 关键字
  * 同步阻塞

* 监视器概念（不需要考虑加索，保证线程安全）
  * 监视器是只包含私有域的类
  * 每个监视器类的对象有一个相关的锁
  * 使用该锁对所有的方法进行加锁
  * 该锁可以有任意多个相关的条件

* Volatile域

* 原子性

* 锁测试与超时


#### lambda
    (String first, String second) -> {
      if ... return ...
      else retrun ...
    }


* 函数式接口

* 方法引用

      Array.sort(strings, String::compareToIgnoreCase)

      System.out::println 等于 x -> System.out.println(x)

*  构造器引用


      ArrayList<String> names = ...;
      Stream<Person> stream = name.stream.map(Person：：new)
      List<person> people = steam.collect(Collect.tolist())

* 变量作用域
  * lambda
    1. 一个代码块
    2. 参数
    3. 自由变量的值，这里指非参数而且不再代码中定义的变量
