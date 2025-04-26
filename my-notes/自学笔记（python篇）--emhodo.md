> - `random.randrange(1,1000)`表示随机产生一个1-1000的整数（含左侧1，但不含右侧1000）。
> - `for in range(10)`  将0-9依次遍历到i

案例1：打印出100以内的所有质数。

`
for i in range (2,100):

>关于质数运算，取值范围从2到平方根取整加一

def is_prime(n):            # 定义 is_prime()，接收一个参数
    if n < 2:              # 开始使用接收到的那个参数（值）开始计算……
        return False       # 不再是返回给人，而是返回给调用它的代码……
    if n == 2:
        return True
    for m in range(2, int(n**0.5)+1):  #***********关于此处为什么用平方根取整再加一，由于质数因数的对称性，以平方根分界，较小的因数与较大因数是呈配对关系的，也就是如果到达平方根取整仍然没有因数，那么再往后也不会有因数的存在了。
        if (n % m) == 0:
            return False
    else:
        return True


>对于数字，我们可用的操作符有 +、-、*、/、//、%、** —— 它们分别代表加、减、乘、除（得几余几）、商（平时用的的除法）、余（只有余数）、幂。

>range、list、generator：

>range的语法：

range(stop)
range(start, stop)
range(start, stop, step)
start：起始值（默认是 0）
stop：结束值（不包含在结果中）
step：步长（默认是 1）

>list（列表推导式）

[表达式 for 变量 in 可迭代对象 if 条件]

# 生成 0~9 的平方数列表
squares = [x**2 for x in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# 只保留偶数的平方
even_squares = [x**2 for x in range(10) if x % 2 == 0]
print(even_squares)  # [0, 4, 16, 36, 64]


>生成器表达式（Generator Expression）

# 和列表推导式几乎一样，只是 方括号换成圆括号

(表达式 for 变量 in 可迭代对象 if 条件)

# 创建生成器对象（不立即计算）
squares_gen = (x**2 for x in range(10))

# 使用时逐个取值
for val in squares_gen:    // val只是个变量名，和i、num啥的都一样
    print(val)
>Compare List Comprehension and Generator Expression

# 特性	          List Comprehension	     Generator Expression
使用括号	          []（方括号）             	 ()（圆括号）
是否立刻执行	      是（立即生成整个列表）    	 否（返回生成器对象）
是否占用大量内存	  是（数据量大时）	             否（非常节省内存）
是否可重复遍历	  是	                     否，只能遍历一次
适合使用场景	      需要保存数据、反复使用	     只读一次、处理大型数据流


>tuple（元组）、set（集合） 和 dict（字典）:

>tuple（元组）

# 语法  
t = (1, 2, 3)

# 示例：
point = (10, 20)
print(point[0])  # 10

# 特点：
属性	    说明
有序	    元素有！！！！固定顺序！！！！
不可变	元素不能修改、添加或删除
支持索引	可以用 t[0] 获取元素
可嵌套	可以包含其他元组、列表等结构
可哈希	可以作为字典的 key、放入 set


>set (集合)

# 语法 
s = {1, 2, 3} 大括号
或使用构造函数：
s = set([1, 2, 3])

# 示例

a = {1, 2, 3}
b = {3, 4, 5}
print(a | b)  # 并集：{1, 2, 3, 4, 5}
print(a & b)  # 交集：{3}
print(a - b)  # 差集：{1, 2}

# 特点
属性	        说明
无序	        元素没有固定顺序
唯一性	    自动去重，！！！！！！不允许重复元素！！！！！！！
可变	        可以添加或删除元素
不支持索引	不能用下标访问元素
支持集合运算	并集、交集、差集、对称差等操作




>dict（字典）

# 语法
d = {"name": "Alice", "age": 25}
或使用 dict()：
d = dict(name="Alice", age=25)
# 示例
user = {
    "name": "Bob",
    "age": 30,
    "email": "bob@example.com"
}

print(user["name"])  # Bob

user["age"] = 31      # 修改值
user["gender"] = "M"  # 添加键值对

# 特点
属性	                        说明
键值对结构	                由 key: value 组成
键唯一	                    每个键只能出现一次
无序（Python 3.7+ 有插入顺序）	遍历顺序是插入顺序
可变	                        可增删改值
键不可变	                    键必须是不可变类型（如 str, int, tuple）


# tuple（元组）、set（集合） 和 dict（字典）对比总结：

特性/结构	 tuple	            set	                 dict
是否有序	      ✅ 是	            ❌ 否（无序）	     ✅ 是（3.7+ 插入顺序）
是否可变	      ❌ 否	            ✅ 是	             ✅ 是
是否支持索引	  ✅ 是	            ❌ 否	             ❌ 只支持键访问
是否支持去重	  ❌ 否	            ✅ 自动去重	         ❌ 通过键唯一实现
常用用途	      数据打包	        数据去重、集合操作	     键值映射、结构化存储
是否可嵌套	  ✅ 是          	✅（嵌套不可变元素）	 ✅ 是

tuple 是一组不可拆的、固定顺序的物品组合，比如 (长, 宽, 高)。
set   是一个只关心内容、不关心顺序、不能重复的元素袋子，比如参加活动的唯一用户 ID。
dict  就像一个电话簿，名字是 key，电话号码是 value。

>数值计算的操作符优先级最高，其次是逻辑操作符，布尔值的操作符优先级最低。


# 字符串，有三种操作：

拼接：+ 和 ' '（后者是空格）
拷贝：*
逻辑运算：in、not in；以及，<、<=、>、>=、!=、==




