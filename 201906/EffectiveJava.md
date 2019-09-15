#### 使用Build构建对象，（参数不定时）
#### 创建或重用对象
#### 消除过期的对象：
* 清空对象引用应该是一种例外，而不是一种规范行为。
* 只要类是自己管理内存，就应该警惕内存泄漏问题
* 缓存 -> WeakHashMap， LinkedHashMap, java.lang.ref
* 监听器和其他回调
* Heap Profiler 等工具

#### 避免使用终结方法
* 终结方法不可预测，很危险，一般情况下是不必要
* 不应该依赖终结方法来更新重要的持久状态
* 使用终结方法有一个非常严重的性能损失

### 对所有对象都通用的方法
#### 覆盖equal是请遵守通用约定
* 类的每个实例本质上是唯一的
* 不关心类是否提供了“逻辑相等”的测试功能
* 超类以及覆盖了equal， 从超类继承过来的行为对于子类也是适合的。
* 类是私有的或是包级私有的，可以确定他的equal方法永远不会被调用

euqal方法实现了等价关系
* 自反性
* 对称性
* 传递性
* 一致性
* 对任何非Null的值引用x, x.equal(null)必须返回false。
    * o == null instanceof getclass


#### 覆盖equals时总要覆盖hashCode方法
#### 始终覆盖toString
2333, Java里面的toString难用的要死
#### 谨慎地覆盖clone
1.  无需调用构造器就可以创建对象
协变返回类型 covariant return type
好麻烦，不想用

#### comparable

+ sgn(x.compareTo(y) == -sgn(y.compareTo(x))) 抛异常时表现一样
+ 可传递的：（x.compareTo(y) > 0 && y.compareTo(z) > 0暗示x.compareTo(z) > 0
+ sgn(x.compareTo(z)) == sgn(y.compareTo(z))
+ (x.compareTo(y)==0)==(x.euqal(y)), 如违反这个条件，应基于说明

+ 自反性 对称性 传递性
