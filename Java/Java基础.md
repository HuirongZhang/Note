Java基础

###### 1.接口和抽象类

- 行为模型应该总是通过接口而不是抽象类定义，所以通常是优先选用接口，尽量少用抽象类。
- 选择抽象类的时候通常是如下情况：需要定义子类的行为，又要为子类提供通用的功能。

###### 2.Java泛型

- 类型参数必须是一个合法的标识符，习惯上使用单个大写字母，通常情况下，K 表示键，V 表示值，E 表示异常或错误，T 表示一般意义上的数据类型。

###### 3.堆

`     // jdk1.8 用lambda: 默认升序排列：o1 < o2 -> o1 - o2 < 0，降序排列：o2 - o1
    PriorityQueue<Integer> pq = new PriorityQueue<>((o1, o2) -> o1 - o2);
    // jdk1.6 用匿名类: 默认升序排列：o1 - o2，降序排列：o2 - o1
    static PriorityQueue<Integer> pq1 = new PriorityQueue<>(new Comparator<Integer>() {
        @Override
        public int compare(Integer o1, Integer o2) {
            return o1 - o2;
        }`



**PriorityQueue 插入元素**



` private void siftUpUsingComparator(int k, E x) {
        while (k > 0) {
            int parent = (k - 1) >>> 1;
            Object e = queue[parent];
            if (comparator.compare(x, (E) e) >= 0)
                break;
            queue[k] = e;
            k = parent;
        }
        queue[k] = x;
    }`









