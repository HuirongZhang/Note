# 第二章

1.定于于函数体内的内置类型没有初始化则其值未定义。

2.如果想在多个文件之间共享const对象，必须定义前加extern。

3.假设n是一个具有负值的int，则表达式string.size()<n几乎肯定为true。这是因为负数n会自动转换为一个比较大的无符号值。