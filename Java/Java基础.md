Java基础

#### 1.接口和抽象类

- 行为模型应该总是通过接口而不是抽象类定义，所以通常是优先选用接口，尽量少用抽象类。
- 选择抽象类的时候通常是如下情况：需要定义子类的行为，又要为子类提供通用的功能。

#### Java 为什么不支持多继承？

c++首先引入的多重继承带来了诸如菱形继承一类的问题，而后为了解决这个问题又不得不引入了虚继承这种概念。然而在实际的应用中人们发现继承更多的只被用在两种场合：扩充/改善基类，以及实现多态。对于前者，单继承足以；而对于后者，则真正需要的其实是纯抽象类，即只包含纯虚函数的基类。而对于这一种基类，由于其目的和普通的实例类已经有所不同，因此在java中将其改称为interface，即接口加以明确区分。

因此，java或者c#所谓的不支持多重继承，只是不支持对实例类的多重继承——因为这种继承所带来的一点点代码上的缩减远比不上其引入的麻烦，但是对于用于实现多态的多重继承，即implement interface依然是很好的支持了的。



作者：Chen Moore
链接：https://www.zhihu.com/question/24317891/answer/65133373
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

C++继承分析

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190116230607742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW8zNDA0,size_16,color_FFFFFF,t_70)

图片来源https://blog.csdn.net/c_base_jin/article/details/86036185

#### 2.Java泛型

- 类型参数必须是一个合法的标识符，习惯上使用单个大写字母，通常情况下，K 表示键，V 表示值，E 表示异常或错误，T 表示一般意义上的数据类型。

#### 3.堆

`     // jdk1.8 用lambda: 默认升序排列：o1 < o2 -> o1 - o2 < 0，降序排列：o2 - o1
    PriorityQueue<Integer> pq = new PriorityQueue<>((o1, o2) -> o1 - o2);
    // jdk1.6 用匿名类: 默认升序排列：o1 - o2，降序排列：o2 - o1
    static PriorityQueue<Integer> pq1 = new PriorityQueue<>(new Comparator<Integer>() {
        @Override
        public int compare(Integer o1, Integer o2) {
            return o1 - o2;
        }`

#### 4.Java集合框架

https://lazydog036.gitee.io/2020/10/29/JAVA集合框架/#Collections工具类



#### 5.volidate

对于被voildate修饰过的变量大部分人都知道当一个线程修改过后对另外一个线程可见，具体是为什么资料的讲解比较少，通过读并发编程的艺术对voildate变量的原理机制做下总结。

  对于voildate变量来讲是有两个语义的，一个是可见性问题，另外一个是禁止指令重排。

 1、可见性问题

​    相对于内存，CPU的速度是极高的，如果CPU需要存取数据时都直接与内存打交道，在存取过程中，CPU将一直空闲，这是一种极大的浪费，所以，现代的CPU里都有很多寄存器，多级cache，他们比内存的存取速度高多了。某个线程执行时，内存中的一份数据，会存在于该线程的工作存储中（working memory，是cache和寄存器的一个抽象，每个线程都有自己的工作存储），并在某个特定时候回写到内存。单线程时，这没有问题，如果是多线程要同时访问同一个变量呢？内存中一个变量会存在于多个工作存储中，线程1修改了变量a的值什么时候对线程2可见？此外，编译器或运行时为了效率可以在允许的时候对指令进行重排序，重排序后的执行顺序就与代码不一致了，这样线程2读取某个变量的时候线程1可能还没有进行写入操作呢，虽然代码顺序上写操作是在前面的。这就是可见性问题的由来。

 使用voildate变量，当写的时候，JMM会把该线程对应的本地内存中的共享变量值刷新到主内存中去，如果读时，JMM会把该线程对应的本地内存置为无效，会直接从内存中去读。

2、禁止重排序

   加上voildate之后，voildate之后的变量不会排到前面去。

 不管是可见性问题还是禁止指令重排，底层都是通过加lock的方式来构建的一个内存屏障来做的

#### 6.反射

#### 7.注解

- https://blog.csdn.net/qq_20009015/article/details/106038023
- https://www.race604.com/annotation-processing/

## 

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510163723241.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzIwMDA5MDE1,size_16,color_FFFFFF,t_70)