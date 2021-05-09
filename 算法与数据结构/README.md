











##### 0.目录

| 分 类          | 题 目                                                        | 难 度 | 题解                    |
| -------------- | ------------------------------------------------------------ | ----- | ----------------------- |
| Array          | [剑指 Offer 03. 数组中重复的数字](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/) | E     | [点击跳转](#锚点剑指03) |
| Array          | [剑指 Offer 04. 二维数组中的查找](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/) | M     | [点击跳转](#锚点剑指04) |
| Two Pointer    | [3.无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/) | M     | [点击跳转](#锚点名2)    |
| Two Pointer    | [11.盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/) | M     | [点击跳转](#锚点名11)   |
| Stack          | [20. 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/) | E     | [点击跳转](#锚点名20)   |
| Array \|Matrix | [74. 搜索二维矩阵](https://leetcode-cn.com/problems/search-a-2d-matrix/) | M     | [点击跳转](#锚点名74)   |
| Tree           | [101. 对称二叉树](https://leetcode-cn.com/problems/symmetric-tree/) | E     | [点击跳转](#锚点名101)  |
| Tree           | [104.二叉树的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/) | E     | [点击跳转](#锚点名104)  |
| Tree           | [110.平衡二叉树](https://leetcode-cn.com/problems/balanced-binary-tree/) | E     | [点击跳转](#锚点名110)  |
| Tree           | [111. 二叉树的最小深度](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/) | E     |                         |
| Tree           | [112.路径总和](https://leetcode-cn.com/problems/path-sum/)   | M     |                         |
| Tree           | [113.路径总和 II](https://leetcode-cn.com/problems/path-sum-ii/) | M     |                         |
| Stack          | [155. 最小栈](https://leetcode-cn.com/problems/min-stack/)   | E     |                         |
| LinkedList     | [206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/) | E     |                         |
| Stack          | [225. 用队列实现栈](https://leetcode-cn.com/problems/implement-stack-using-queues/) | E     |                         |
| Tree           | [226.翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/) | E     |                         |
| Queue          | [232. 用栈实现队列](https://leetcode-cn.com/problems/implement-queue-using-stacks/) | E     |                         |
| Array\|Matrix  | [240. 搜索二维矩阵 II](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/) | M     |                         |
| Array          | [283. 移动零](https://leetcode-cn.com/problems/move-zeroes/) | E     |                         |
| Tree           | [404. 左叶子之和](https://leetcode-cn.com/problems/sum-of-left-leaves/) | E     |                         |
| Tree           | [437. 路径总和 III](https://leetcode-cn.com/problems/path-sum-iii/) | M     |                         |
| Array          | [485. 最大连续 1 的个数](https://leetcode-cn.com/problems/max-consecutive-ones/) | E     |                         |
| Array\|Matrix  | [503. 下一个更大元素 II](https://leetcode-cn.com/problems/next-greater-element-ii/) | M     |                         |
| Tree           | [543.二叉树的直径](https://leetcode-cn.com/problems/diameter-of-binary-tree/) | E     |                         |
| Array\|Matrix  | [566. 重塑矩阵](https://leetcode-cn.com/problems/reshape-the-matrix/) | E     |                         |
| Tree           | [572. 另一个树的子树](https://leetcode-cn.com/problems/subtree-of-another-tree/) | E     |                         |
| Tree           | [617.合并二叉树](https://leetcode-cn.com/problems/merge-two-binary-trees/) | E     |                         |
| dfs            | [687. 最长同值路径](https://leetcode-cn.com/problems/longest-univalue-path/) | M     |                         |
| Stack          | [739. 每日温度](https://leetcode-cn.com/problems/daily-temperatures/) | M     |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |
|                |                                                              |       |                         |



#### 

###### <a id="锚点剑指03">剑指 Offer 03. 数组中重复的数字</a>

分析：题目限定数组长度n，数组中的值在 0～n-1 的范围内

方法一：

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int [] tags=new int[nums.length];
        int res=-1;
        for(int i=0;i<nums.length;i++){
            tags[nums[i]]++;
            if(tags[nums[i]]>1){
                res=nums[i];
                break;
            }
        }
        return res;
    }
}
```

方法二：

当条件 **`nums[i]!=i`**和**`nums[i]==nums[nums[i]]`**同时满足时说明在两个不同的索引位置 **`i`** 和 **`nums[i]`** 出现了相同的数字，**nums[i]**重复



```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        for(int i=0;i<nums.length;i++){
           if(nums[i]!=i){
                if(nums[i]==nums[nums[i]]){
                    return nums[i];
                }
                /*Swap*/
                int temp=nums[i];
                nums[i]=nums[temp];
                nums[temp]=temp;
            }
        }
        return -1;
    }
}
```



```
/*---------*/
当重复数字是0时这种方法不通过
测试用例:[2, 3, 1, 0, 0, 5]
		测试结果:-1
		期望结果:0
/*---------*/
```



###### <a id="锚点剑指04">剑指 Offer 04. 二维数组中的查找</a>



```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int m=matrix.length,n=matrix[0].length; //m-行数 n-列数
        int i=0,j=n-1;
        while(i<m&&j>=0){
            if(target==matrix[i][j]){
                return true;
            }
            else if(target>matrix[i][j]){
                i++;
            }else {
                j--;
            }
        }
        return false;
    }
}
```



###### <a id="锚点名2">3.无重复字符的最长子串</a>

解析：**滑动窗口** --**滑动窗口算法**的本质是**双指针法中的左右指针法**,滑动窗口算法是双指针法中的左右指针法更为形象的一种表达方式。

滑动窗口算法可以用以解决**数组、字符串**的**子元素**问题。所谓滑动窗口，就像描述的那样，可以理解成是一个会滑动的窗口，每次记录下窗口的状态，再找出符合条件的适合的窗口。它可以将嵌套的循环问题，更高效的解决。

找出从l开始的最长不重复子串，res存储最大长度，r指示子串的结尾，用set存储子串中的字符，r每次移动将字符加入set

优化1，当剩余长度已经小于res，提前结束

优化2，左指针每次移动时直接移到内层循环退出时导致重复的那个字符后一位

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
       Set<Character> set=new HashSet<>();//存储从l到r的子串字符
        int l=0,r=0,res=0;
        while(l<s.length()){
            if(res>s.length()-l-1)//长度减1才是下标
                break;//提前结束
            while(r<s.length()&&!set.contains(s.charAt(r))){
                set.add(s.charAt(r));
                r++;
            }
            res=Math.max(res,r-l);
            while(r<s.length()&&set.contains(s.charAt(r))){//
                set.remove(s.charAt(l));
                l++;
            }
        }
        return res;
    }
}
```



###### <a id="锚点名11">11.盛最多水的容器</a>

```java
int l=0,r=height.length-1,res=0;
while(l<r){
      res= height[l]<height[r] ? Math.max(res,height[l++]*(r-l)):Math.max(res,height[r--]*(r-l));//l++先执行了错误
}
   return res;  
```

​     踩的一个坑--先`height[l++]`   再 `(r-l)`  导致 `l++` 已经执行再计算的 `l-r`

解析：双指针

```java
   public int maxArea(int[] height) {
     int l=0,r=height.length-1,res=0;
        while(l<r){
            res= height[l]<height[r] ? Math.max(res,(r-l)*height[l++]):Math.max(res,(r-l)*height[r--]);
        }
        return res;
    }
```



###### <a id="锚点名20">20.有效的括号</a>

```java
public boolean isValid(String s) {
        Stack<Character> stack=new Stack<>();
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='('||s.charAt(i)=='['||s.charAt(i)=='{'){
                stack.push(s.charAt(i));
            }else {
                if(stack.empty()) return false;
                if(s.charAt(i)==')'){
                    if(stack.peek()!='('){
                        return false;
                    }
                }
                if(s.charAt(i)==']'){
                    if(stack.peek()!='['){
                        return false;
                    }
                }
                if(s.charAt(i)=='}'){
                    if(stack.peek()!='{'){
                        return false;
                    }
                }
                stack.pop();
            }
        }
        return stack.empty();
    }
```



###### <a id="锚点名74">74.搜索二维矩阵</a>

行数`m = matrix.length`,列数`n = matrix[0].length`

由于矩阵每一行拼接在上一行的末尾，则会得到一个升序数组。所以基本思路还是通过将二维转化为一维数组来解决。

```java
public boolean searchMatrix(int[][] matrix, int target) {
        int low=0;
        int m=matrix.length;//行数
        int n=matrix[0].length;//列数
        int high=m*n-1;
        while (low<=high){
            int mid=(high-low)/2+low;//等同于（high+low)/2 防止溢出
            if(target==matrix[mid/n][mid%n]){
                return true;
            }else if(target>matrix[mid/n][mid%n]){
                low=mid+1;
            }else{
                high=mid-1;
            }
        }
        return false;
    }
```



###### <a id="锚点名101">101.对称二叉树</a>

```java
class Solution {    public boolean isSymmetric(TreeNode root) {        if(root==null) return true;        return dfs(root.left,root.right);    }    public boolean dfs(TreeNode A,TreeNode B){        if(A==null&&B==null) return true;        if(A==null||B==null) return false;        if(A.val!=B.val) return false;        return dfs(A.left,B.right)&&dfs(A.right,B.left);    }}
```



###### <a id="锚点名104">104.二叉树的最大深度</a>

```java
class Solution {    public int maxDepth(TreeNode root) {        if(root==null) return 0;        return Math.max(maxDepth(root.left),maxDepth(root.right))+1;    }}
```

###### <a id="锚点名110">110.平衡二叉树</a>



解析：递归求二叉树最大深度时检验是否存在不平衡。

```java
class Solution {private boolean result = true;public boolean isBalanced(TreeNode root) {    maxDepth(root);    return result;}public int maxDepth(TreeNode root) {    if (root == null) return 0;    int l = maxDepth(root.left);    int r = maxDepth(root.right);    if (Math.abs(l - r) > 1) result = false;    return 1 + Math.max(l, r);}}
```

###### [111. 二叉树的最小深度](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/)

解析:

叶子节点的定义是左孩子和右孩子都为 null 时叫做叶子节点

- 当 root 节点左右孩子都为空时，返回 1
- 当 root 节点左右孩子有一个为空时，返回不为空的孩子节点的深度，因为这时只要有一个子节点不为空则不是叶子节点还需要往下寻找
- 当 root 节点左右孩子都不为空时，返回左右孩子较小深度的节点值

```java
class Solution {      public int minDepth(TreeNode root) {        if(root==null) return 0;        int ldepth=minDepth(root.left);        int rdepth=minDepth(root.right);        if(ldepth==0||rdepth==0)  return ldepth+rdepth+1;//左右孩子有一个为空时，返回不为空的孩子节点的深度        return Math.min(ldepth,rdepth)+1;    }  }
```



###### 112.[路径总和](https://leetcode-cn.com/problems/path-sum/)

判断是否存在从根节点到叶子节点值和等于target，终止条件--叶子节点且节点值等于target遍历下来的剩余值不满足终止条件时，左右子树递归寻找。

```java
class Solution {    public boolean hasPathSum(TreeNode root, int targetSum) {        if(root==null) return false;        if(root.left==null&&root.right==null&&root.val==targetSum) return true;        return (hasPathSum(root.left,targetSum-root.val)||hasPathSum(root.right,targetSum-root.val));    }}
```

###### 113.[路径总和 II](https://leetcode-cn.com/problems/path-sum-ii/)

和112.[路径总和](https://leetcode-cn.com/problems/path-sum/)的不同在于需要把所有满足条件的路径返回，考虑把深度优先搜索，把路径依次加入结果，若不满足终止条件则剔除

```java
class Solution {    List<List<Integer>> res=new ArrayList<>();    List<Integer> path=new ArrayList<>();    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {       dfs(root,0,targetSum);       return res;    }    public void dfs(TreeNode root,int pathSum,int sum){         if(root==null) return ;         pathSum+=root.val;         path.add(root.val);         if(root.left==null&&root.right==null&&pathSum==sum)            res.add(new ArrayList<>(path));        dfs(root.left,pathSum,sum);        dfs(root.right,pathSum,sum);        path.remove(path.size()-1);////恢复现场，因为targetSum是局部变量，故无须恢复现场    }}
```

###### [155. 最小栈](https://leetcode-cn.com/problems/min-stack/)

解析:辅助栈minStack 每次入栈出栈都维持当前最小值在栈顶

```java
class MinStack {    private Stack<Integer> dataStack;    private Stack<Integer> minStack;    private Integer min;    /** initialize your data structure here. */    public MinStack() {        dataStack=new Stack<>();        minStack=new Stack<>();        min=Integer.MAX_VALUE;    }        public void push(int x) {        dataStack.push(x);        min=Math.min(min,x);        minStack.push(min);            }        public void pop() {        dataStack.pop();        minStack.pop();        min=minStack.isEmpty()?Integer.MAX_VALUE : minStack.peek();    }        public int top() {        return dataStack.peek();    }        public int getMin() {        return min;    }}
```

###### [206. 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

```java
class Solution {    public ListNode reverseList(ListNode head) {        ListNode pre=new ListNode(0);//虚拟头节点        ListNode p=head;//工作指针        ListNode next=null;//存储工作指针下一个节点        while(p!=null){            next=p.next;            p.next=pre.next;            pre.next=p;            p=next;        }        return pre.next;    }}
```



###### 226.[翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/)

```java
class Solution {    public TreeNode invertTree(TreeNode root) {        if(root==null) return null;        TreeNode temp=root.right;        root.right=root.left;        root.left=temp;        invertTree( root.left);        invertTree(root.right);        return root;    }}
```

###### [225. 用队列实现栈](https://leetcode-cn.com/problems/implement-stack-using-queues/)

```java
class MyStack {    private Queue<Integer> queue;    /** Initialize your data structure here. */    public MyStack() {         queue = new LinkedList<>();    }        /** Push element x onto stack. */    public void push(int x) {        queue.add(x);        int cnt=queue.size();        while(cnt-->1){            queue.add(queue.poll());        }    }        /** Removes the element on top of the stack and returns that element. */    public int pop() {        return queue.poll();    }        /** Get the top element. */    public int top() {        return queue.peek();    }        /** Returns whether the stack is empty. */    public boolean empty() {        return queue.isEmpty();    }}
```



###### [232. 用栈实现队列](https://leetcode-cn.com/problems/implement-queue-using-stacks/)

```java
class MyQueue {    private Stack<Integer> in = new Stack<>();    private Stack<Integer> out = new Stack<>();    /** Initialize your data structure here. */    public MyQueue() {    }        /** Push element x to the back of queue. */    public void push(int x) {        in.push(x);    }        /** Removes the element from in front of queue and returns that element. */    public int pop() {        if (out.isEmpty()) {//假如out栈为空则把in栈全部送入out            while (!in.isEmpty()) {                out.push(in.pop());            }        }        return out.pop();//若out不为空直接取栈顶    }        /** Get the front element. */    public int peek() {        if (out.isEmpty()) {//假如out栈为空则把in栈全部送入out            while (!in.isEmpty()) {                out.push(in.pop());            }        }        return out.peek();    }        /** Returns whether the queue is empty. */    public boolean empty() {        return in.isEmpty() && out.isEmpty();    }}
```

###### [240. 搜索二维矩阵 II](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/)

```java
class Solution {    public boolean searchMatrix(int[][] matrix, int target) {        int m=matrix.length;//行数        int n=matrix[0].length;//列数        int i=m-1,j=0;        while (i>=0&&j<=n-1){            if(target==matrix[i][j]){                return true;            }else if(target>matrix[i][j]){                j++;            }else{                i--;            }        }        return false;    }}
```



###### [283. 移动零](https://leetcode-cn.com/problems/move-zeroes/)

**方法一**：使用双指针，左指针指向当前已经处理好的序列的尾部，右指针指向待处理序列的头部。

右指针不断向右移动，每次右指针指向非零数，则将左右指针对应的数交换，同时左指针右移。

- 左指针左边均为非零数；

- 右指针左边直到左指针处均为零。

因此每次交换，都是将左指针的零与右指针的非零数交换，且非零数的相对顺序并未改变。

```java
class Solution {    public void moveZeroes(int[] nums) {        int n = nums.length, left = 0, right = 0;        while (right < n) {            if (nums[right] != 0) {                swap(nums, left, right);                left++;            }            right++;        }    }    public void swap(int[] nums, int left, int right) {        int temp = nums[left];        nums[left] = nums[right];        nums[right] = temp;    }}
```

**方法二**：遍历过程中把非零数字按新计数index装进nums,最后再把index之后的全部填充为0

```java
class Solution {    public void moveZeroes(int[] nums) {        int index=0;        for(int n:nums){            if(n!=0){                nums[index++]=n;            }        }        while(index<nums.length){            nums[index++]=0;        }    }}
```



###### [404. 左叶子之和](https://leetcode-cn.com/problems/sum-of-left-leaves/)

**递归法三部曲**

- 确定递归函数的参数和返回值
- 确定终止条件
- 确定单层递归的逻辑

```java
class Solution {    public int sumOfLeftLeaves(TreeNode root) {//从左往右计算左叶子节点之和        if(root==null) return 0;        if(isLeaf(root.left)) return root.left.val+sumOfLeftLeaves(root.right);//左叶子节点需从父节点开始判断        return sumOfLeftLeaves(root.left)+sumOfLeftLeaves(root.right);    }    public boolean isLeaf(TreeNode node){//判断叶子节点        if(node==null) return false;        if(node.left==null&&node.right==null) return true;        return false;    }}
```



###### [437. 路径总和 III](https://leetcode-cn.com/problems/path-sum-iii/)

解析：首先我们的思路还是dfs,这里比较特殊的是起点不必是根节点，终点也不必是叶子节点，现在我们假设某一节点node，计算从node节点出发满足条件的路径条数 = node本身是否是一条 + `dfs(node.left,tempsum)+dfs(node.right,tempsum)`；但是在主方法我们还需要递归计算root左右子树所有节点开始的路径条数，所以结果+`pathSum(root.left,sum)+pathSum(root.right,sum)`.

```java
class Solution {        public int pathSum(TreeNode root, int sum) {         int res=0;        if(root==null) return res;               res=dfs(root,sum)+pathSum(root.left,sum)+pathSum(root.right,sum);          return res;      }    public int dfs(TreeNode node, int sum){        int res=0;        if(node==null) return res;        if(node.val==sum) res++;        res+=dfs(node.left,sum-node.val)+dfs(node.right,sum-node.val);        return res;    }}
```

###### [485. 最大连续 1 的个数](https://leetcode-cn.com/problems/max-consecutive-ones/)

```java
class Solution {    public int findMaxConsecutiveOnes(int[] nums) {       int maxCount = 0, count = 0;        int n = nums.length;        for (int i = 0; i < n; i++) {            if (nums[i] == 1) {                count++;            } else {                maxCount = Math.max(maxCount, count);                count = 0;            }        }        maxCount = Math.max(maxCount, count);        return maxCount;    }}
```



###### [503. 下一个更大元素 II](https://leetcode-cn.com/problems/next-greater-element-ii/)

```java
class Solution {    public int[] nextGreaterElements(int[] nums) {        Stack<Integer> st =new Stack<>();        int[] next = new int[nums.length];        Arrays.fill(next,-1);        for(int i=0;i<2*nums.length-1;i++){            while(!st.isEmpty()&&nums[i%nums.length]>nums[st.peek()]){                next[st.pop()]=nums[i%nums.length];            }            st.push(i%nums.length);        }        return next;    }}
```



###### 543.[二叉树的直径](https://leetcode-cn.com/problems/diameter-of-binary-tree/) 

解析：递归求二叉树最大深度时保存最大直径

```Java
class Solution {    int max=0;    public int diameterOfBinaryTree(TreeNode root) {        if(root==null) return 0;        MaxDepth(root);        return max;    }    public int MaxDepth(TreeNode root){        if(root==null) return 0;        int leftdepth=MaxDepth(root.left);        int rightdepth=MaxDepth(root.right);        max=Math.max(max,leftdepth+rightdepth);        return Math.max(leftdepth,rightdepth)+1;    }}
```

###### [566. 重塑矩阵](https://leetcode-cn.com/problems/reshape-the-matrix/)

思路与算法

对于一个行数为 m，列数为 n，行列下标都从 00 开始编号的二维数组，我们可以通过下面的方式，将其中的每个元素 (i, j)(i,j) 映射到整数域内，并且它们按照行优先的顺序一一对应着 [0, mn)中的每一个整数。形象化地来说，我们把这个二维数组「排扁」成了一个一维数组。如果读者对机器学习有一定了解，可以知道这就是flatten 操作。

这样的映射即为：

$$
(i, j) \to i \times n+j
(i,j)→i×n+j
$$
同样地，我们可以将整数 x 映射回其在矩阵中的下标，

​	
$$
\begin{cases}
i=x / n
\\
j=x \% n
\\
\end{cases}
$$


```Java
class Solution {    public int[][] matrixReshape(int[][] nums, int r, int c) {        int m=nums.length,n=nums[0].length;//原矩阵的行数、列数        if(m*n!=r*c)    return nums;        int[][] reshapedNums = new int[r][c];        int index=0;        for(int i=0;i<r;i++){            for(int j=0;j<c;j++){                reshapedNums[i][j]=nums[index/n][index%n];//                index++;            }        }        return reshapedNums;    }}
```



###### [572. 另一个树的子树](https://leetcode-cn.com/problems/subtree-of-another-tree/)

解析：与543.[二叉树的直径](https://leetcode-cn.com/problems/diameter-of-binary-tree/) 类似，对二叉树s的子树，不仅可以从root开始，也可以从子节点开始，这类都需要在主方法递归计算左右子树

```java
class Solution {    public boolean isSubtree(TreeNode s, TreeNode t) {        if(s==null) return false;//需判断s是否为空是因为下面获取了s.left和s.right，否则会空指针异常        return dfs(s,t)||isSubtree(s.left,t)||isSubtree(s.right,t);    }    public boolean dfs(TreeNode s, TreeNode t){        if(s==null&&t==null) return true;        if(s==null||t==null) return false;        if(s.val!=t.val) return false;        return dfs(s.left,t.left)&&(dfs(s.right,t.right));    }}
```



###### 617.[合并二叉树](https://leetcode-cn.com/problems/merge-two-binary-trees/)

```java
class Solution {    public TreeNode mergeTrees(TreeNode root1, TreeNode root2) {        if(root1==null&&root2==null) return null;        if(root1==null) return root2;        if(root2==null) return root1;        TreeNode root=new TreeNode(root1.val+root2.val);        root.left=mergeTrees(root1.left,root2.left);        root.right=mergeTrees(root1.right,root2.right);        return root;    }}
```

###### [687. 最长同值路径](https://leetcode-cn.com/problems/longest-univalue-path/)

解析：分析某一节点node 为根节点的子树 最长同值路径，需求出

left=node左子树的最长同值路径

right=node右子树的最长同值路径

然后有以下3种情况：

- 左右子节点val都等于node  则left+right+2
- 左节点val==node.val  右节点val不等于  或者反过来  则是 left+1||right+1
- 左、右子节点都不等于，则不需要把node连上去



```java
class Solution {    int ans=0;    public int longestUnivaluePath(TreeNode root) {        if(root==null) return 0;        dfs(root);        return ans;    }    public int dfs(TreeNode node){        if(node==null) return 0;        int lpath=dfs(node.left);        int rpath=dfs(node.right);        int maxpath=0;//以当前node为起点的最大同值路径        if(node.left!=null&&node.left.val==node.val&&node.right!=null&&node.right.val==node.val){            ans=Math.max(ans,lpath+rpath+2);//左右子树都相同的情况        }        if(node.left!=null&&node.left.val==node.val) {//只有左子树相同的情况            maxpath=lpath+1;        }        if(node.right!=null&&node.right.val==node.val){//只有右子树相同的情况,可能左子树的计算过，需对比大小            maxpath=Math.max(maxpath,rpath+1);        }        ans=Math.max(ans,maxpath);//假如是左右子树相同的情况取ans        return maxpath;    }}
```



```java
class Solution {    int res=0;    public int longestUnivaluePath(TreeNode root) {               if(root==null) return res;        dfs(root);        return res;    }    public int dfs(TreeNode node){        if(node==null)  return 0;        int l=dfs(node.left);//左子节点目前的最长路径长度        int r=dfs(node.right);//右子节点目前的最长路径长度        int arrowLeft=0,arrowRight=0;//从节点 node 延伸出的最长箭头的长度        if(node.left!=null&&node.left.val==node.val) arrowLeft=l+1;        if(node.right!=null&&node.right.val==node.val) arrowRight=r+1;        res=Math.max(res,arrowLeft+arrowRight);//当左右子树中存在一条与node值不一样的路径时，其arrow值为0        return Math.max(arrowLeft, arrowRight);    }}
```



###### [739. 每日温度](https://leetcode-cn.com/problems/daily-temperatures/)

解析：维护一个单调栈（元素不增，为什么是用栈而不是队列），存储元素下标，栈内元素表示尚未找到比它大的数据，一旦遇到则出栈，并计算索引差值。

```java
class Solution {    public int[] dailyTemperatures(int[] T) {        Stack<Integer> st=new Stack<>();        int []ans=new int [T.length];        for(int i=0;i<T.length;i++){            while(!st.isEmpty()&&T[i]>T[st.peek()]){                ans[st.peek()]=i-st.pop();            }            st.push(i);        }        return ans;    }}
```



