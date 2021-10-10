JAVA学习笔记

[TOC]



## JAVA基础篇

### IDEA快捷键

![image-20210708091820312](D:\myTypora\typora-pic\image-20210708091820312.png)

![image-20210708091833544](D:\myTypora\typora-pic\image-20210708091833544.png)

![image-20210708091852999](D:\myTypora\typora-pic\image-20210708091852999.png)



### 常用的转义字符

在控制台，输入 tab 键，可以实现命令补全

\t ：一个制表位，实现对齐的功能

\n ：换行符

\\\:一个\

\\":一个"

\ \'：一个'

\r:一个回车，光标回到本行最前面，System.out.println("韩顺平教育\r北京"),将输出北京平教育。

### java开发注意事项

![image-20211010210809385](D:\myTypora\typora-pic\image-20211010210809385.png)

### 文档注释

![image-20210630152232373](D:\myTypora\typora-pic\image-20210630152232373.png)

文件夹名时生成的javadoc的存储路径-xx  -yy是开头的author和version之类的东西。

### 新手应遵守的代码规范

![image-20210630152423507](D:\myTypora\typora-pic\image-20210630152423507.png)

### 数据类型

![image-20210816190205835](D:\myTypora\typora-pic\image-20210816190205835.png)

上述只是数据的类型，都可以用十进制二进制八进制或十六进制表示。

### float和double有关IEEE标准问题：

https://blog.csdn.net/k346k346/article/details/50487127

![image-20210701103606394](D:\myTypora\typora-pic\image-20210701103606394-16338695389132.png)

### char类型细节

![image-20210701103857130](D:\myTypora\typora-pic\image-20210701103857130.png)

![image-20210701103907547](D:\myTypora\typora-pic\image-20210701103907547.png)

### 类型转换

#### 自动类型转换

![image-20211010210915073](D:\myTypora\typora-pic\image-20211010210915073.png)

特殊情况：

1. byte b = 10;

   这种情况可能会想10是个int型怎么能赋值给byte呢？实际上当把一个数赋值给byte时编译器会先判断是否属于-128~127,如果属于则可以赋值。

   但是这种情况不可以：

   int n = 1;

   byte b = n;

   这种情况下n已经是int型了，直接进行类型判断，而不是上述判断

   同理short也是先进行数值范围判断再进行类型判断。

   但是float和double不行

#### 强制类型转换



自动类型转换的逆过程，***\*将容量大的数据类型转换为容量小的数据类型\****。使用时要加上强制转换符 ( )，但可能造成***\*精度降低或溢出\****,格外要注意。

![image-20211010210937556](D:\myTypora\typora-pic\image-20211010210937556.png)

#### 基本数据类型和String类的转换

![image-20211010210950840](D:\myTypora\typora-pic\image-20211010210950840.png)

特殊情况：

复合赋值运算符以及自增自减为什么可以通过编译？

有人可能会觉得int怎么可以赋值给byte

byte b = 3;

b += 2; //实际等价于b = (byte)(b + 2)

b++; //实际等价于b = (byte)(b + 1)

即底层会有一个强制类型转换

### 自增自减的坑

![image-20211010211137240](D:\myTypora\typora-pic\image-20211010211137240.png)

注意规则，我们平时前面都是另一个变量所以不影响，但本质的运算规则是这三步。不要以为第一题是2

### 两大编程思想

看空心金字塔程序。

public class ForExercise {

//编写一个 main 方法

public static void main(String[] args) {

//打印 1~100 之间所有是 9 的倍数的整数，统计个数	及 总和.[化繁为简,先死后活]

//老韩的两个编程思想(技巧)

//1. 化繁为简 : 即将复杂的需求，***\*拆解成简单的需求\****，逐步完成	编程 = ***\*思想\**** ***\*--\*******\*练习\*******\*->\****  ***\*代码\****

//2. 先死后活 : 先考虑固定的值，然后转成可以灵活变化的值

//

//思路分析

//打印 1~100 之间所有是 9 的倍数的整数，统计个数	及 总和

//化繁为简

//(1) 完成 输出 1-100 的值

//(2) 在输出的过程中，进行过滤，只输出 9 的倍数	i % 9 ==0

//(3) 统计个数 定义一个变量 int count = 0; 当 条件满足时 count++;

//(4) 总和 ,  定义一个变量 int sum = 0;  当条件满足时累积 sum += i;

//先死后活

//(1) 为了适应更好的需求，把范围的开始的值和结束的值，做出变量

//(2) 还可以更进一步 9  倍数也做成变量 int t = 9;

 //个人感悟：有点类似模块化思想，有利于后期代码维护。

 

int count = 0; //统计 9 的倍数个数 变量

int sum = 0; //总和int start = 10;

int end = 200; int t = 5; // 倍数

for(int i = start; i <= end; i++) {

if( i % t == 0) { System.out.println("i=" + i); count++;

sum += i;//累积

}

}

System.out.println("count=" + count); System.out.println("sum=" + sum);

}

}



### 数组的定义和初始化

![image-20210703091231892](D:\myTypora\typora-pic\image-20210703091231892.png)

使用方式 2-动态初始化 

1.先声明数组 

语法:数据类型 数组名[]; 也可以 数据类型[] 数组名; 

int a[]; 或者 int[] a; 

2.创建数组 

语法: 数组名 = new 数据类型[大小]; 

a = new int[10]; 

使用方式 3-静态初始化

![](D:\myTypora\typora-pic\image-20210703091538302.png)

注意：数组的空间的一开始就确定的，后面无法随意更改。注意和ArrayList对比、

### 类与对象（基础）

#### jvm中内存分配情况*

对象是存储在堆中，对象的引用是在栈中，值为堆中对象的地址。

![image-20210704094833123](D:\myTypora\typora-pic\image-20210704094833123.png)

![image-20210704094721099](D:\myTypora\typora-pic\image-20210704094721099.png)

p1.age = 80;

![image-20210704094729215](D:\myTypora\typora-pic\image-20210704094729215.png)

内存分配流程：

Person p = new Person();

p.name = “jack”;

p.age = 10；

1) 先加载 Person 类信息(属性和方法信息, 只会加载一次)

2) 在堆中分配空间, 进行默认初始化(看规则)

3) 把地址赋给 p , p 就指向对象 

4) 进行指定初始化， 比如 p.name =”jack” p.age = 10 

注意：运行时常量池一直在方法区（Method Area)，里面包含了每一个.class文件中的常量池中的内容。而字符串常量池在**Java 7之前保存在方法区**，在**Java 7之后保存在堆上**。

#### 内存分布图

 Java 内存的结构分析

程序计数器：用来记录正在执行的虚拟机字节码指令地址。可通过改变这个计数器的值来选取下一条需要执行的字节码指令。

Java虚拟机栈：线程私有，生命周期与线程相同，每当创建一个线程时，JVM就会为这个线程创建一个对应的java栈。在这个java栈中又会包含多个栈帧，每运行一个方法就创建一个栈帧，用于存储局部变量表、操作栈、方法返回值等。每一个方法从调用直至执行完成的过程，就对应一个栈帧在java栈中入栈到出栈的过程。

本地方法栈：与虚拟机栈发挥的作用相似，区别在于：虚拟机栈为虚拟机执行java方法（也就是字节码）服务，本地方法栈为虚拟机使用到的Native方法服务。

堆：存储**对象实例以及数组**。是垃圾收集器管理的主要区域。java堆可以处于物理上不连续的内存空间，只要逻辑上连续即可。

方法区：用于存放类信息（如类名、访问修饰符等）、常量池、静态变量、即时编译器便宜后的代码等。虽然JVM规范把方法区描述为堆的一个逻辑部分， 但它却有个别名non-heap（非堆），目的应该是与Java堆区分开来。　

![img](D:\myTypora\typora-pic\70.png)



#### 传参机制

注意java中基本数据类型只有值传递，并不能使用&号取地址;引用类型的传递只有数组和对象。

##### 基本数据类型传参机制

值传递主要是因为在栈中新创建了一个空间，在这个空间中操作形参影响不到另一个栈空间的实参。

![image-20210704142357978](D:\myTypora\typora-pic\image-20210704142357978.png)

![image-20210704142406999](D:\myTypora\typora-pic\image-20210704142406999.png)

##### 引用类型传参机制

引用类型传递的是地址（传递也是值，但是值是地址），可以通过形参影响实参！

主要是因为新创建空间中形参的值为实参值的地址，所以形参改变会影响实参。

例子1（传数组）：

![image-20210704142514688](D:\myTypora\typora-pic\image-20210704142514688.png)

例子二（传对象）：

![image-20210704142522049](D:\myTypora\typora-pic\image-20210704142522049.png)

#### 方法调用细节

![image-20210704155637804](D:\myTypora\typora-pic\image-20210704155637804.png)

#### 递归调用时自增自减的坑：

递归实现斐波那契数列：

public class Demo {
	public static void main(String[] args){
		Solution A = new Solution();
		System.out.print(A.fibnaci(10));
	}
} 

class Solution {
	public int fibnaci(int n){
		if(n == 1)
			return 1;
		else 
			return (fibnaci(--n) + 1) * 2;（此处假若是n--就不行）
	}
}

如果变成n--的话，那么每次递归调用传递进去的参数永远是10，会导致栈溢出。（用内存分析法分析）。

#### 可变参数

//1. int... 表示接受的是可变参数，类型是 int ,即可以接收多个 int(0\-多)

//2. 使用可变参数时，可以当做数组来使用 即 nums 可以当做数组

//3. 遍历 nums 求和即可

public int sum(int... nums) {

​		//System.out.println("接收的参数个数=" \+ nums.length);

​			int res = 0;

​			for(int i = 0; i < nums.length; i++) {

​				res += nums[i];

​			}

​				return res;

}

}

![image-20210706084320705](D:\myTypora\typora-pic\image-20210706084320705.png)



#### 作用域

![image-20210706090737722](D:\myTypora\typora-pic\image-20210706090737722.png)

#### 构造器

[修饰符] 方法名(形参列表){ 

方法体; 

} 

类似于c++中的构造函数。

注意事项和使用细节

![image-20210706094646434](D:\myTypora\typora-pic\image-20210706094646434.png)

![image-20210706094649821](D:\myTypora\typora-pic\image-20210706094649821.png)

#### 有构造器时候对象的创建流程*（同jvm中内存分配情况*对比）

![image-20210706103842521](D:\myTypora\typora-pic\image-20210706103842521.png)

![image-20210706103853428](D:\myTypora\typora-pic\image-20210706103853428.png)



#### this指针问题

哪个对象调用，this就指向谁。this代表对象，也可以调用方法。

![image-20210706140426495](D:\myTypora\typora-pic\image-20210706140426495.png)

使用细节

![image-20210706142232774](D:\myTypora\typora-pic\image-20210706142232774.png)

### 类与对象（中级）

#### 包：

##### 包的作用

![image-20210708104835893](D:\myTypora\typora-pic\image-20210708104835893.png)

##### 包的本质分析

![image-20210708104904848](D:\myTypora\typora-pic\image-20210708104904848.png)

##### 包的命名规则

![image-20210708104933122](D:\myTypora\typora-pic\image-20210708104933122.png)

##### 常用的包

![image-20210708105002405](D:\myTypora\typora-pic\image-20210708105002405.png)

##### 如何引入包

![image-20210708105038647](D:\myTypora\typora-pic\image-20210708105038647.png)

##### 包中类的方法互相调用

![image-20210708105220504](D:\myTypora\typora-pic\image-20210708105220504.png)

![image-20210708105121748](D:\myTypora\typora-pic\image-20210708105121748.png)

#### 访问修饰符

![image-20210708110743354](D:\myTypora\typora-pic\image-20210708110743354.png)

注意上述的是不能之间访问，但是可以通过方法间接访问。

如果不使用继承，那么想访问另一个类的属性就需要通过实例化对象，用对象来调用，子类那一列的规则就不用看了。

如果使用了继承那么四列都需要看。比如说，父类和子类在同一个包，虽然默认访问修饰符在子类那一列为×，但是由于同处一个包，那么子类仍然可以直接访问父类的默认访问属性。

#### 封装

三步骤：

![image-20210708153024861](D:\myTypora\typora-pic\image-20210708153024861.png)

#### 继承

##### 继承的原因![image-20210708153059869](D:\myTypora\typora-pic\image-20210708153059869.png)

##### 继承的语法

![image-20210708153132129](D:\myTypora\typora-pic\image-20210708153132129.png)

##### 继承的细节

![image-20210709094403374](D:\myTypora\typora-pic\image-20210709094403374.png)

![image-20210709094424490](D:\myTypora\typora-pic\image-20210709094424490.png)

##### 继承的本质

![image-20210709100837659](D:\myTypora\typora-pic\image-20210709100837659.png)

内存布局：

![image-20210709100915553](D:\myTypora\typora-pic\image-20210709100915553.png)

1.加载类信息从顶级父类向下加载

2.分配堆内存空间

3.从顶级父类开始初始化(注意只有new才会创建对象，构造器只起初始化作用。)

4.将内存地址赋值给栈中对象的引用。

上述堆中的方块就是**子类**的堆内存空间。



查找过程：（查找顺序注意上图方法区的箭头，从本类往父类找）

package com.hspedu.extend_; 

/

**

\* 

讲解继承的本质 

*

/ 

public class ExtendsTheory { 

public static void main(String[] args) { 

Son son = new Son();

**//这时请大家注意，要按照查找关系来返回信息** 

**//(1) 首先看子类是否有该属性** 

**//(2) 如果子类有这个属性，并且可以访问，则返回信息** 

**//(3) 如果子类没有这个属性，就看父类有没有这个属性(如果父类有该属性，并且可以访问，就返回信息..)** 

**//(4) 如果父类没有就按照(3)的规则，继续找上级父类，直到 Object...** 

**//提示：如果查找过程中，找到了，但是不能访问，则报错，cannot access**，**查找过程中断。**

​				**如果查找方法的过程中，没有找到，则提示方法不存在。**

**//方法的查找过程和属性查找过程一模一样**

System.out.println(son.name);//返回就是大头儿子 

//System.out.println(son.age);//返回的就是 39 

//System.out.println(son.getAge());//返回的就是 39 

System.out.println(son.hobby);//返回的就是旅游 } 

}

class GrandPa { //爷类 

String name = "大头爷爷"; 

String hobby = "旅游"; 

}

class Father extends GrandPa {//父类 

String name = "大头爸爸"; 

private int age = 39; 

public int getAge() { 

return age; } 

}

class Son extends Father { //子类 

String name = "大头儿子"; }



练习题：

![image-20210709103040978](D:\myTypora\typora-pic\image-20210709103040978.png)

1由于this不能和super共存，于是执行this("abc")。

2.执行B的有参构造函数，此时执行super()，调转到A的无参构造函数。

3.输出a后在输出b name 最后输出b

##### super关键字

基本语法：

![image-20210709142252080](D:\myTypora\typora-pic\image-20210709142252080.png)

细节

![image-20210709142400879](D:\myTypora\typora-pic\image-20210709142400879.png)

![image-20210709142405390](D:\myTypora\typora-pic\image-20210709142405390.png)

##### super和this比较![image-20210709142443938](D:\myTypora\typora-pic\image-20210709142443938.png)



##### 重写

![image-20210709144334268](D:\myTypora\typora-pic\image-20210709144334268.png)

细节

![image-20210709144449107](D:\myTypora\typora-pic\image-20210709144449107.png)

##### 重载和重写比较

![image-20210709145243583](D:\myTypora\typora-pic\image-20210709145243583.png)

#### 多态

##### 重写重载体现多态

package com.hspedu.

poly_; 

public class PloyMethod { 

public static void main(String[] args) { 

//方法重载体现多态 

A a = new A(); 

//这里我们传入不同的参数，就会调用不同 sum 方法，就体现多态 

System.out.println(a.sum(10, 20)); 

System.out.println(a.sum(10, 20, 30)); 

//方法重写体现多态 

B b = new B(); 

a.say(); 

b.say(); 

} 

}

class B { //父类 

public void say() { 

System.out.println("B say() 方法被调用..."); } 

}

class A extends B {//子类 

public int sum(int n1, int n2){//和下面 sum 构成重载 

return n1 + n2; 

}

public int sum(int n1, int n2, int n3){ 

return n1 + n2 + n3; 

}

public void say() { 

System.out.println("A say() 方法被调用..."); } 

}

##### 对象多态**(**核心，困难，重点)

举个例子：

![image-20210710092054604](D:\myTypora\typora-pic\image-20210710092054604.png)

如果动物很多，食物很多，那么Master类中一种动物以及食物的组合需定义一个feed方法，代码复用性不高，不利于维护和管理。如：

//主人给小狗 喂食 骨头

public void feed(Dog dog, Bone bone) { 

// System.out.println("主人 " \+ name + " 给 " \+ dog.getName() + " 吃 " \+ bone.getName()); // } 

// //主人给 小猫喂 黄花鱼 

// public void feed(Cat cat, Fish fish) { 

// System.out.println("主人 " \+ name + " 给 " \+ cat.getName() + " 吃"\+ fish.getName()); // }



利用多态后：

public void feed(Animal animal, Food food) { 

System.out.println("主人 " \+ name + " 给 " \+ animal.getName() + " 吃 " \+ food.getName()); }

//animal 编译类型是 Animal,可以指向(接收) Animal 子类的对象 

//food 编译类型是 Food ,可以指向(接收) Food 子类的对象

只需要定义一个feed方法传进来不同的animal以及food的子类就行。

![image-20210710091310371](D:\myTypora\typora-pic\image-20210710091310371.png)

![image-20210710091321927](D:\myTypora\typora-pic\image-20210710091321927.png)

##### 多态细节

###### 向上转型：

![image-20210710095336945](D:\myTypora\typora-pic\image-20210710095336945.png)

因为在编译阶段，能调用哪些成员,是由编译类型来决定的，所以不能调用子类特有成员、

最终运行效果看子类(运行类型)的具体实现, 即调用方法时，按照从子类(运行类型)开始查找方法 

然后调用，规则我前面我们讲的方法调用规则一致。



###### 向下转型：

![image-20210710095347368](D:\myTypora\typora-pic\image-20210710095347368.png)

Cat cat = (Cat) animal; 

cat.catchMouse();//猫抓老鼠

animal只能访问animal的方法和属性，但是不能访问cat特有的方法和属性

但通过这样向下转型后cat可以访问animal和cat所有的方法和属性（遵守访问权限）



###### 属性重写问题：

属性没有重写之说！属性的值看编译器：**属性看编译类型，方法看运行类型**。

package com.hspedu.poly_.detail_; 

public class PolyDetail02 { 

public static void main(String[] args) { 

Base base = new Sub();//向上转型 

System.out.println(base.count);// ？ 看编译类型 10 

Sub sub = new Sub(); 

System.out.println(sub.count);//? 20 } 

}

class Base { //父类 

int count = 10;//属性 

}

class Sub extends Base {//子类 

int count = 20;//属性 

}



###### instance问题

instanceOf 比较操作符，用于判断对象的运行类型是否为 XX 类型或 XX 类型的子类型



###### 动态绑定机制（非常非常重要）

![image-20210710104105387](D:\myTypora\typora-pic\image-20210710104105387.png)

public class DynamicBinding { 

public static void main(String[] args) { 

//a 的编译类型 A, 运行类型 B 

A a = new B();//向上转型 

System.out.println(a.sum());//?40 \-\> 30 （注释掉B中的sum和sum1后的结果。）

System.out.println(a.sum1());//?30\-\> 20（注释掉B中的sum和sum1后的结果。）

 } 

}

class A {//父类 

public int i = 10; //动态绑定机制: 

public int sum() {//父类 sum() 

return getI() + 10;//20 + 10 

}

public int sum1() {//父类 sum1() 

return i + 10;//10 + 10 

}

public int getI() {//父类 getI 

return i; } 

}

class B extends A {//子类 

public int i = 20; 

// public int sum() { 

// return i + 20; 

// }

public int getI() {//子类 getI() 

return i; 

} 

// public int sum1() { 

// return i + 10; 

// } 

}

###### 多态应用1-多态数组

数组的定义类型为父类类型，里面保存的实际元素类型为子类类型

应用实例:现有一个继承结构如下：要求创建 1 个 Person 对象、2 个 Student 对象和 2 个 Teacher 对象, 统

一放在数组 中，并调用每个对象 say 方法

. 

应用实例升级：如何调用子类特有的方法，比如 Teacher 有一个 teach , Student 有一个 study 怎么调用？ 

![image-20210710110549868](D:\myTypora\typora-pic\image-20210710110549868.png)

![image-20210710110607888](D:\myTypora\typora-pic\image-20210710110607888.png)

![image-20210710110617151](D:\myTypora\typora-pic\image-20210710110617151.png)

###### 多态应用2-多态参数

![image-20210710144623803](D:\myTypora\typora-pic\image-20210710144623803.png)

![image-20210710144801623](D:\myTypora\typora-pic\image-20210710144801623.png)

![image-20210710144825424](D:\myTypora\typora-pic\image-20210710144825424.png)

![image-20210710144836604](D:\myTypora\typora-pic\image-20210710144836604.png)

![image-20210710144857755](D:\myTypora\typora-pic\image-20210710144857755.png)

#### Object中的方法

##### equals方法

![image-20210711084905983](D:\myTypora\typora-pic\image-20210711084905983.png)

![image-20210711084912625](D:\myTypora\typora-pic\image-20210711084912625.png)

##### hashCode方法

![image-20210711094201381](D:\myTypora\typora-pic\image-20210711094201381.png)

![image-20210711094241837](D:\myTypora\typora-pic\image-20210711094241837.png)

##### toString

![image-20210711094818933](D:\myTypora\typora-pic\image-20210711094818933.png)

![image-20210711094825258](D:\myTypora\typora-pic\image-20210711094825258.png)



##### finalize（新版本java已经弃用）

![image-20210711100305647](D:\myTypora\typora-pic\image-20210711100305647.png)

### 面向对象（高级）

#### 类变量（静态变量）（记忆顺序 概念->使用场景->调用方式->细节）

##### 类变量概念

![image-20210714084756831](D:\myTypora\typora-pic\image-20210714084756831.png)

![image-20210714084841806](D:\myTypora\typora-pic\image-20210714084841806.png)

1.同一个类所有对象共享这个变量。

2.在类加载的时候就生成了，即使没有创建对象实例也可以访问。

jdk8之前放在方法区的静态域中，jdk8（包括8）后放在栈中。

##### 类变量内存布局

![image-20210714084824620](D:\myTypora\typora-pic\image-20210714084824620.png)

##### 类变量使用细节

![image-20210714085948039](D:\myTypora\typora-pic\image-20210714085948039.png)

![image-20210714085958801](D:\myTypora\typora-pic\image-20210714085958801.png)

#### 类方法（记忆顺序 概念->使用场景->调用方式->细节）

##### 概念

![image-20210714090820450](D:\myTypora\typora-pic\image-20210714090820450.png)

![image-20210714090827234](D:\myTypora\typora-pic\image-20210714090827234.png)

##### 类方法使用场景

![image-20210714091642323](D:\myTypora\typora-pic\image-20210714091642323.png)

##### 类方法使用细节

![image-20210714091659383](D:\myTypora\typora-pic\image-20210714091659383.png)

![image-20210714091706093](D:\myTypora\typora-pic\image-20210714091706093.png)

 如果想在静态方法中调用非静态的成员，需要通过实例化对象以对象名来调用

因为非静态的成员和对象是有关联的，不同对象的非静态成员可能不同。

而静态成员所有对象共同维护，所有和对象无关，直接通过类名调用即可。

静态方法可以被继承但是不能被重写。

#### main语法

![image-20210714100541279](D:\myTypora\typora-pic\image-20210714100541279.png)

![image-20210714100900944](D:\myTypora\typora-pic\image-20210714100900944.png)

#### 代码块

##### 概念

![image-20210714105720305](D:\myTypora\typora-pic\image-20210714105720305.png)

##### 使用方法

![image-20210714105734354](D:\myTypora\typora-pic\image-20210714105734354.png)

##### 使用场景和好处

![image-20210714105750633](D:\myTypora\typora-pic\image-20210714105750633.png)

##### 细节

![image-20210714105806011](D:\myTypora\typora-pic\image-20210714105806011.png)

![image-20210714112026837](D:\myTypora\typora-pic\image-20210714112026837.png)

![image-20210714112035561](D:\myTypora\typora-pic\image-20210714112035561.png)

![image-20210714112041799](D:\myTypora\typora-pic\image-20210714112041799.png)

#### 创建对象时的执行顺序（***）：

##### 当没有继承关系时：

1.加载类信息

在这一步中将执行静态代码块以及静态属性的初始化

**2.对象的创建（流程如下）：**

先去执行构造器，但此时注意，构造器的前面**隐含**着普通代码块以及非静态属性的初始化流程。

**执行完普通代码块以及非静态属性的初始化后再执行构造器中的内容。**

3.把对象地址赋给引用。

这个流程和上述细节4一样

##### 当有继承关系时：

1.加载类信息

先加载父类再加载子类，所以先执行父类的静态代码块以及静态属性的初始化，再执行子类的静态代码块以及静态属性的初始化。

**2.创建对象（流程如下）：**

先去执行子类的构造器但因为有继承关系第一行有隐含的super，所以又去执行父类的构造器直到object（每一个构造器中都有隐含的super,object没有内容，所以都是看自己定义的最顶级的父类）

到顶级父类的构造器后，有隐藏的普通代码块以及非静态属性的初始化，执行完毕后再执行构造器中的内容，然后返回到子类的隐藏的普通代码块以及非静态属性的初始化，最后执行子类的构造器内容内容

3.把对象地址赋给引用。

这个流程和上述细节6一样

public AA{

​	public AA(){

//隐藏的super

//隐藏的普通代码块以及普通属性初始化

构造器内容

}

}

public BB extends AA{

​	public BB(){

​	//隐藏的super

​	//隐藏的普通代码块以及普通属性初始化

构造器内容

}

}

#### 单例模式

![image-20210715082131999](D:\myTypora\typora-pic\image-20210715082131999.png)

![image-20210715082217229](D:\myTypora\typora-pic\image-20210715082217229.png)

##### 饿汉式（可能造成创建了对象但是没有使用）

class GirlFriend { 

private String name；

//public static int n1 = 100; 

//为了能够在静态方法中，返回 gf 对象，需要将其修饰为 static 

//對象，通常是重量級的對象, 餓漢式可能造成創建了對象，但是沒有使用. 

private static GirlFriend gf = new GirlFriend("小红红"); 

//如何保障我们只能创建一个 GirlFriend 对象 

//步骤[单例模式\-饿汉式] 

//1. 将构造器私有化 

//2. 在类的内部直接创建对象(该对象是 static) 

//3. 提供一个公共的 static 方法，返回 gf 对象 

private GirlFriend(String name) { 

System.out.println("構造器被調用."); 

this.name = name; 

}

public static GirlFriend getInstance() { 

return gf; 

}

@Override 

public String toString() { 

return "GirlFriend{" \+ "name='" \+ name + '\'' \+ '}'; } 

##### 懒汉式

public class SingleTon02 { 

public static void main(String[] args) { 

//new Cat("大黃"); 

//System.out.println(Cat.n1); 

Cat instance = Cat.getInstance(); System.out.println(instance); //再次調用 getInstance 

Cat instance2 = Cat.getInstance(); 

System.out.println(instance2); 

System.out.println(instance == instance2);//T 

} 

}

//希望在程序運行過程中，只能創建一個 Cat 對象 

//使用單例模式 

class Cat { 

private String name; 

public static int n1 = 999; 

private static Cat cat ; //默認是 null 

//步驟 

//1.仍然構造器私有化 

//2.定義一個 static 靜態屬性對象 

//3.

提供一個 public 的 static 方法，可以返回一個 Cat 對象 

//4.懶漢式，只有當用戶使用 getInstance 時，才返回 cat 對象, 後面再次調用時，會返回上次創建的 cat 對象 

// 從而保證了單例 

private Cat(String name) { 

System.out.

println("構造器調用..."); 

this.name = name; 

}

public static Cat getInstance() { 

if(cat == null) {//如果還沒有創建 cat 對象 

cat = new Cat("小可愛"); 

}

return cat; 

}

@Override 

public String toString() { 

return 

"Cat{" \+ "name='" \+ name + '\'' \+ '}'; 

} 

} 

##### 饿汉式和懒汉式对比

![image-20210715083911450](D:\myTypora\typora-pic\image-20210715083911450.png)

#### final关键字

##### 概念

![image-20210715091812014](D:\myTypora\typora-pic\image-20210715091812014.png)

##### 细节

![image-20210715091828559](D:\myTypora\typora-pic\image-20210715091828559.png)

![image-20210715091835250](D:\myTypora\typora-pic\image-20210715091835250.png)

#### 抽象类

##### 概念

![image-20210715095034650](D:\myTypora\typora-pic\image-20210715095034650.png)

##### 细节

![image-20210715095056888](D:\myTypora\typora-pic\image-20210715095056888.png)

![image-20210715095120472](D:\myTypora\typora-pic\image-20210715095120472.png)

![image-20210715095133358](D:\myTypora\typora-pic\image-20210715095133358.png)

private是私有的，继承后不能访问和重写。

final修饰的方法本身就是不能重写。

我们只定义静态static方法完全OK，因为静态方法是属于类的，所以静态方法必须满足给类调用，如果通过类无法调用，那么这种静态方法肯定是不对的。为了达到这一要求，static方法就必须有方法体，即已经实现了，也就不是抽象方法了。

构造器不能被abstrct修饰，因为构造器不能被继承，而abstrct修饰方法目的就是为了被子类实现。

#### 接口

##### 概念

![image-20210715142539224](D:\myTypora\typora-pic\image-20210715142539224.png)

##### 快速入门

![image-20210715142559655](D:\myTypora\typora-pic\image-20210715142559655.png)

![image-20210715142610854](D:\myTypora\typora-pic\image-20210715142610854.png)

![image-20210715142624956](D:\myTypora\typora-pic\image-20210715142624956.png)

![image-20210715142635142](D:\myTypora\typora-pic\image-20210715142635142.png)

![image-20210715142642601](D:\myTypora\typora-pic\image-20210715142642601.png)

上面其实还有一个Computer类

public Computer{

​	public void work(Interface interface){

​		interface.start();

​		interface.stop();

}

}

##### 细节

![image-20210715142839638](D:\myTypora\typora-pic\image-20210715142839638.png)

![image-20210715143619859](D:\myTypora\typora-pic\image-20210715143619859.png)

##### 例子

![image-20210715144111803](D:\myTypora\typora-pic\image-20210715144111803.png)

##### 接口和继承的对比

![image-20210715150042947](D:\myTypora\typora-pic\image-20210715150042947.png)

继承下来的东西你可以直接用，但是接口中的方法你需要去实现。

![image-20210715151255037](D:\myTypora\typora-pic\image-20210715151255037.png)

#### 内部类（**）

##### 概念

![image-20210716085248485](D:\myTypora\typora-pic\image-20210716085248485.png)

![image-20210716085303072](D:\myTypora\typora-pic\image-20210716085303072.png)

##### 分类

![image-20210716085314848](D:\myTypora\typora-pic\image-20210716085314848.png)

##### 局部内部类

![image-20210716090245229](D:\myTypora\typora-pic\image-20210716090245229.png)

![image-20210716090251794](D:\myTypora\typora-pic\image-20210716090251794.png)





##### 匿名内部类**

![image-20210716092816522](D:\myTypora\typora-pic\image-20210716092816522.png)

###### 基于接口的匿名内部类

![image-20210716092938482](D:\myTypora\typora-pic\image-20210716092938482.png)

![image-20210716092948824](D:\myTypora\typora-pic\image-20210716092948824.png)

![image-20210716093007771](D:\myTypora\typora-pic\image-20210716093007771.png)





###### 基于类的匿名内部类

![image-20210716100511988](D:\myTypora\typora-pic\image-20210716100511988.png)

![image-20210716100522456](D:\myTypora\typora-pic\image-20210716100522456.png)

![image-20210716100534604](D:\myTypora\typora-pic\image-20210716100534604.png)

![image-20210716100748416](D:\myTypora\typora-pic\image-20210716100748416.png)

![image-20210716100751972](D:\myTypora\typora-pic\image-20210716100751972.png)

![image-20210716100755159](D:\myTypora\typora-pic\image-20210716100755159.png)

###### 使用场景--当作实参传递

![image-20210716100823938](D:\myTypora\typora-pic\image-20210716100823938.png)

![image-20210716100835889](D:\myTypora\typora-pic\image-20210716100835889.png)





##### 成员内部类

###### 概念

![image-20210716110240309](D:\myTypora\typora-pic\image-20210716110240309.png)



![image-20210716110244275](D:\myTypora\typora-pic\image-20210716110244275.png)

![image-20210716110254340](D:\myTypora\typora-pic\image-20210716110254340.png)

###### 使用方法

![image-20210716110547281](D:\myTypora\typora-pic\image-20210716110547281-163387111747815.png)

![image-20210716110555960](D:\myTypora\typora-pic\image-20210716110555960.png)

![image-20210716110606329](D:\myTypora\typora-pic\image-20210716110606329.png)

![image-20210716110614689](D:\myTypora\typora-pic\image-20210716110614689.png)

![image-20210716110633501](D:\myTypora\typora-pic\image-20210716110633501.png)

##### 静态内部类

###### 概念

![image-20210716111323796](D:\myTypora\typora-pic\image-20210716111323796.png)

![image-20210716111327167](D:\myTypora\typora-pic\image-20210716111327167.png)

![image-20210716111333282](D:\myTypora\typora-pic\image-20210716111333282.png)

![image-20210716111337296](D:\myTypora\typora-pic\image-20210716111337296.png)

###### 使用方法

![image-20210716111350052](D:\myTypora\typora-pic\image-20210716111350052.png)

![image-20210716111358854](D:\myTypora\typora-pic\image-20210716111358854.png)

![image-20210716111411288](D:\myTypora\typora-pic\image-20210716111411288.png)

![image-20210716111420795](D:\myTypora\typora-pic\image-20210716111420795.png)

![image-20210716111429088](D:\myTypora\typora-pic\image-20210716111429088.png)

### 枚举

两种实现方式：

1) 自定义类实现枚举 

2) 使用 enum 关键字实现枚举

#### 自定义枚举

![image-20210716142417354](D:\myTypora\typora-pic\image-20210716142417354.png)



![image-20210716142505867](D:\myTypora\typora-pic\image-20210716142505867.png)

1) 构造器私有化 

2) 本类内部创建一组对象[四个 春夏秋冬] 

3) 对外暴露对象（通过为对象添加 public final static 修饰符） 

4) 可以提供 get 方法，但是不要提供 set

#### enum枚举

![image-20210716143222271](D:\myTypora\typora-pic\image-20210716143222271.png)

![image-20210716143230312](D:\myTypora\typora-pic\image-20210716143230312.png)

![image-20210716143239421](D:\myTypora\typora-pic\image-20210716143239421.png)

![image-20210716143251577](D:\myTypora\typora-pic\image-20210716143251577.png)



###### Enum类的成员方法

![image-20210716152257541](D:\myTypora\typora-pic\image-20210716152257541.png)

##### 细节

1) 当我们使用 enum 关键字开发一个枚举类时，默认会继承 Enum 类, 而且是一个 final 类[如何证明],老师使用 javap 工 具来演示 

2) 传统的 public static final Season2 SPRING = new Season2("春天", "温暖"); 简化成 SPRING("春天", "温暖")， 这里必 须知道，它调用的是哪个构造器. 

3) 如果使用无参构造器 创建 枚举对象，则实参列表和小括号都可以省略 

4) 当有多个枚举对象时，使用,间隔，最后有一个分号结尾 

5) 枚举对象必须放在枚举类的行首

![image-20210716143403735](D:\myTypora\typora-pic\image-20210716143403735.png)

##### 枚举实现接口

1) 使用 enum 关键字后，就不能再继承其它类了，因为 enum 会隐式继承 Enum，而 Java 是单继承机制。 

2) 枚举类和普通类一样，可以实现接口，如下形式。 enum 类名 implements 接口 1，接口 2{} 

![image-20210716154410945](D:\myTypora\typora-pic\image-20210716154410945.png)

![image-20210716154421358](D:\myTypora\typora-pic\image-20210716154421358.png)

### 注解

1) 注解(Annotation)也被称为元数据(Metadata)，用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息。 

2) 和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息。 

3) 在 JavaSE 中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在 JavaEE 中注解占据了更重要的角 色，例如用来配置应用程序的任何切面，代替 java EE 旧版中所遗留的繁冗代码和 XML 配置等。

使用 Annotation 时要在其前面增加 @ 符号, 并把该 Annotation 当成一个修饰符使用。用于修饰它支持的程序元素 

三个基本的 Annotation: 

1) @Override: 限定某个方法，是重写父类方法, 该注解只能用于方法 

2) @Deprecated: 用于表示某个程序元素(类, 方法等)已过时 

3) @SuppressWarnings: 抑制编译器警告

#### @Override

![image-20210717135630670](D:\myTypora\typora-pic\image-20210717135630670.png)

![image-20210717135720375](D:\myTypora\typora-pic\image-20210717135720375.png)

#### @Deprecated

![image-20210717140100510](D:\myTypora\typora-pic\image-20210717140100510.png)

即不在推荐使用，但是仍然可以使用

#### @SuppressWarnings

@SuppressWarnings: 抑制编译器警告

![image-20210717140735348](D:\myTypora\typora-pic\image-20210717140735348.png)

关于 SuppressWarnings 作用范围是和你放置的位置相关 

比如 @SuppressWarnings 放置在 main 方法，那么抑制警告的范围就是 main 

通常我们可以放置具体的语句, 方法, 类

(1) 放置的位置就是 TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE

### 元注解

1) Retention //指定注解的作用范围，三种 SOURCE,CLASS,RUNTIME 

2) Target // 指定注解可以在哪些地方使用 

3) Documented //指定该注解是否会在 javadoc 体现 

4) Inherited //子类会继承父类注解

### 异常

#### 概念

![image-20210718084910476](D:\myTypora\typora-pic\image-20210718084910476.png)

#### 异常体系图

![image-20210718090408909](D:\myTypora\typora-pic\image-20210718090408909.png)

![image-20210718090414519](D:\myTypora\typora-pic\image-20210718090414519.png)

#### 五大运行时异常

##### NullPointerException 空指针异常

![image-20210718091423995](D:\myTypora\typora-pic\image-20210718091423995.png)

public class NullPointerException_ { 

​	public static void main(String[] args) { 

​		String name = null; 

​		System.out.println(name.length()); 

} 

}

##### ArithmeticException 数学运算异常

![image-20210718091534744](D:\myTypora\typora-pic\image-20210718091534744.png)

##### ArrayIndexOutOfBoundsException 数组下标越界异常

![image-20210718091554559](D:\myTypora\typora-pic\image-20210718091554559.png)

##### ClassCastException 类型转换异常

![image-20210718091608994](D:\myTypora\typora-pic\image-20210718091608994.png)

![image-20210718091619247](D:\myTypora\typora-pic\image-20210718091619247.png)

##### NumberFormatException 数字格式不正确异常

![image-20210718091644296](D:\myTypora\typora-pic\image-20210718091644296.png)

![image-20210718091658113](D:\myTypora\typora-pic\image-20210718091658113.png)

#### 编译异常

![image-20210718091717554](D:\myTypora\typora-pic\image-20210718091717554.png)

##### 常见的编译异常

![image-20210718091732003](D:\myTypora\typora-pic\image-20210718091732003.png)

#### 异常处理

##### 异常处理方式

![image-20210718092745094](D:\myTypora\typora-pic\image-20210718092745094.png)

![image-20210718092929672](D:\myTypora\typora-pic\image-20210718092929672.png)

![image-20210718094142113](D:\myTypora\typora-pic\image-20210718094142113.png)

##### try-catch异常处理

![image-20210718094641829](D:\myTypora\typora-pic\image-20210718094641829.png)

![image-20210718094657620](D:\myTypora\typora-pic\image-20210718094657620.png)

![image-20210718094713970](D:\myTypora\typora-pic\image-20210718094713970.png)

![image-20210718095057691](D:\myTypora\typora-pic\image-20210718095057691.png)

![image-20210718095106222](D:\myTypora\typora-pic\image-20210718095106222.png)

![image-20210718094723238](D:\myTypora\typora-pic\image-20210718094723238.png)

##### try-catch-finally题目

![image-20210718100730102](D:\myTypora\typora-pic\image-20210718100730102.png)

![image-20210718100740616](D:\myTypora\typora-pic\image-20210718100740616.png)

return ++i虽然不会返回，但是会执行里面的语句

![image-20210718100746120](D:\myTypora\typora-pic\image-20210718100746120.png)



##### try\-catch-finally 执行顺序小结

![image-20210718100942133](D:\myTypora\typora-pic\image-20210718100942133.png)

##### try-catch最佳实践

![image-20210718103858774](D:\myTypora\typora-pic\image-20210718103858774.png)

![image-20210718103908636](D:\myTypora\typora-pic\image-20210718103908636.png)

![image-20210718103925923](D:\myTypora\typora-pic\image-20210718103925923.png)

##### throws异常处理

![image-20210718135933033](D:\myTypora\typora-pic\image-20210718135933033.png)

![image-20210718135952077](D:\myTypora\typora-pic\image-20210718135952077.png)

##### throws异常处理细节

![image-20210718140112726](D:\myTypora\typora-pic\image-20210718140112726.png)

![image-20210718140155118](D:\myTypora\typora-pic\image-20210718140155118.png)

![image-20210718140213192](D:\myTypora\typora-pic\image-20210718140213192.png)

##### 自定义异常

![image-20210718140827620](D:\myTypora\typora-pic\image-20210718140827620.png)

![image-20210718140834357](D:\myTypora\typora-pic\image-20210718140834357.png)

##### 自定义异常实例

![image-20210718140926096](D:\myTypora\typora-pic\image-20210718140926096.png)

![image-20210718140941551](D:\myTypora\typora-pic\image-20210718140941551.png)

![image-20210718140956484](D:\myTypora\typora-pic\image-20210718140956484.png)

![image-20210718141003700](D:\myTypora\typora-pic\image-20210718141003700.png)

##### throws和throw的差别

![image-20210718141137569](D:\myTypora\typora-pic\image-20210718141137569.png)

### 包装类

针对八种基本数据类型相应的引用类型—包装类

![image-20210718150357683](D:\myTypora\typora-pic\image-20210718150357683.png)

![image-20210718150404185](D:\myTypora\typora-pic\image-20210718150404185.png)

![image-20210718150407351](D:\myTypora\typora-pic\image-20210718150407351.png)

![image-20210718150410716](D:\myTypora\typora-pic\image-20210718150410716.png)

#### 包装类和基本数据类型的转换

![image-20210718150941073](D:\myTypora\typora-pic\image-20210718150941073.png)

![image-20210718151039730](D:\myTypora\typora-pic\image-20210718151039730-16338701043094.png)

![image-20210718152319840](D:\myTypora\typora-pic\image-20210718152319840.png)

注意第二个中，三元运算符是一个整体，要提升到级别最高的数据类型，返回的是Double包装类。

#### 包装类和String类的相互转换

以Integer为例

![image-20210718153010868](D:\myTypora\typora-pic\image-20210718153010868.png)

![image-20210718153033746](D:\myTypora\typora-pic\image-20210718153033746.png)

#### Integer 类和 Character 类的常用方法

![image-20210718153511868](D:\myTypora\typora-pic\image-20210718153511868.png)

#### 包装类面试题

![image-20210720082543204](D:\myTypora\typora-pic\image-20210720082543204.png)

只要有基本数据类型，那么==就是判断值是否相等。

### String类

![image-20210720084304627](D:\myTypora\typora-pic\image-20210720084304627.png)

![image-20210720084327750](D:\myTypora\typora-pic\image-20210720084327750.png)

   1.String 对象用于保存字符串，也就是一组字符序列 

2. "jack" 字符串常量, 双引号括起的字符序列 

3. 字符串的字符使用 Unicode 字符编码，一个字符(不区分字母还是汉字)占两个字节 

4. String 类有很多构造器，构造器的重载  常用的有 

   String s1 = new String(); 

   String s2 = new String(String original); 

   String s3 = new String(char[] a); 

​       String s4 = new String(char[] a,int startIndex,int count) 

​	   String s5 = new String(byte[] b) 

5. String 类实现了接口 Serializable【String 可以串行化:可以在网络传输】 接口 Comparable [String 对象可以比较大小] 

6. String 是 final 类，不能被其他的类继承 

7. String 有属性 private final char value[]; 用于存放字符串内容 

8. 一定要注意：value 是一个 final 类型， 不可以修改(需要功力)：即 value 不能指向 新的地址，但是单个字符内容是可以变化

#### 创建String对象的两种方法及内存分析

![image-20210720090435762](D:\myTypora\typora-pic\image-20210720090435762.png)

两种对象的区别

![image-20210720090450488](D:\myTypora\typora-pic\image-20210720090450488.png)

![image-20210720090455995](D:\myTypora\typora-pic\image-20210720090455995.png)

#### 测试题

![image-20210720092140081](D:\myTypora\typora-pic\image-20210720092140081.png)

#### 字符串的特性

![image-20210720093633069](D:\myTypora\typora-pic\image-20210720093633069.png)

![image-20210720093638234](D:\myTypora\typora-pic\image-20210720093638234.png)

#### 面试题

![image-20210720093646612](D:\myTypora\typora-pic\image-20210720093646612.png)

![image-20210720093655984](D:\myTypora\typora-pic\image-20210720093655984.png)

![image-20210720093700441](D:\myTypora\typora-pic\image-20210720093700441.png)

下题很精彩

![image-20210720095141913](D:\myTypora\typora-pic\image-20210720095141913.png)

![image-20210720095147398](D:\myTypora\typora-pic\image-20210720095147398.png)

#### String常用方法

![image-20210720100619118](D:\myTypora\typora-pic\image-20210720100619118.png)

//1. equals 前面已经讲过了. 比较内容是否相同，区分大小写 

String str1 = "hello"; 

String str2 = "Hello"; 

System.out.println(str1.equals(str2));// 



// 2.equalsIgnoreCase 忽略大小写的判断内容是否相等 

String username = "johN"; 

if ("john".equalsIgnoreCase(username)) { 

System.out.println("Success!"); 

} else {

System.out.println("Failure!"); 

}



// 3.length 获取字符的个数，字符串的长度 

System.out.println("韩顺平".length()); 



// 4.indexOf 获取字符在字符串对象中第一次出现的索引，索引从 0 开始，如果找不到，返回-1 

String s1 = "wer@terwe@g";

 int index = s1.indexOf('@'); 

System.out.println(index);// 3 

System.out.println("weIndex=" \+ s1.indexOf("we"));//0 



// 5.lastIndexOf 获取字符在字符串中最后一次出现的索引，索引从 0 开始，如果找不到，返回\-1 

s1 = "wer@terwe@g@"; 

index = s1.lastIndexOf('@'); 

System.out.println(index);//11 

System.out.println("ter 的位置=" \+ s1.lastIndexOf("ter"));//4 



// 6.substring 截取指定范围的子串 

String name = "hello,张三"; //下面 name.substring(6) 从索引 6 开始截取后面所有的内容 

System.out.println(name.substring(6));//截取后面的字符 

//name.substring(0,5)表示从索引 0 开始截取，截取到索引 5-1=4 位置 

System.out.println(name.substring(2,5));//llo 

![image-20210720100626771](D:\myTypora\typora-pic\image-20210720100626771.png)

// 1.toUpperCase 转换成大写 

String s = "heLLo"; 

System.out.println(s.toUpperCase());//HELLO



// 2.toLowerCase 

System.out.println(s.toLowerCase());//hello



// 3.concat 拼接字符串 

String s1 = "宝玉"; 

s1 = s1.concat("林黛玉").concat("薛宝钗").concat("together"); 

System.out.println(s1);//宝玉林黛玉薛宝钗 together



// 4.replace 替换字符串中的字符 

s1 = "宝玉 and 林黛玉 林黛玉 林黛玉"; 

//在 s1 中，将 所有的 林黛玉 替换成薛宝钗 

// 老韩解读: s1.replace() 方法执行后，返回的结果才是替换过的. 

// 注意对 s1 没有任何影响 

String s11 = s1.replace("宝玉", "jack"); 

System.out.println(s1);//宝玉 and 林黛玉 林黛玉 林黛玉 

System.out.println(s11);//jack and 林黛玉 林黛玉 林黛玉



// 5.split 分割字符串, 对于某些分割字符，我们需要 转义比如 | \\等 

String poem = "锄禾日当午,汗滴禾下土,谁知盘中餐,粒粒皆辛苦"; 

//老韩解读： 

// 1. 以 , 为标准对 poem 进行分割 , 返回一个数组 

// 2. 在对字符串进行分割时，如果有特殊字符，需要加入 转义符 \ 

String[] split = poem.split(","); 

poem = "E:\\aaa\\bbb"; 

split = poem.split("\\\\"); 

System.out.println("==分割后内容==="); 

for (int i = 0; i < split.length; i++) { 

System.out.println(split[i]); 

}



// 6.toCharArray 转换成字符数组 

s = "happy"; 

char[] chs = s.toCharArray(); 

for (int i = 0; i < chs.length; i++) { 

System.out.println(chs[i]); 

}



// 7.compareTo 比较两个字符串的大小，如果前者大， 

// 则返回正数，后者大，则返回负数，如果相等，返回 0 

// 老韩解读 

// (1) 如果长度相同，并且每个字符也相同，就返回 0 

// (2) 如果长度相同或者不相同，但是在进行比较时，可以区分大小 

// 就返回 if (c1 != c2) { 

// return c1 \- c2; 

// } 

// (3) 如果前面的部分都相同，就返回 str1.len \- str2.len 

String a = "jcck";// len = 3 

String b = "jack";// len = 4 

System.out.println(a.compareTo(b)); // 返回值是 'c' - 'a' = 2 的值



// 8.format 格式字符串 

/\* 占位符有: 

\* %s 字符串 %c 字符 %d 整型 %.2f 浮点型 

/ 

String name = "john"; 

int age = 10; 

double score = 56.857; 

char gender = '男';

//将所有的信息都拼接在一个字符串. String info ="我的姓名是" \+ name + "年龄是" \+ age + ",成绩是" \+ score + "性别是" \+ gender + "。希望大家喜欢我！ "; 

System.out.println(info); 

//老韩解读 

//1. %s , %d , %.2f %c 称为占位符 

//2. 这些占位符由后面变量来替换 

//3. %s 表示后面由 字符串来替换 

//4. %d 是整数来替换 

//5. %.2f 表示使用小数来替换，替换后，只会保留小数点两位, 并且进行四舍五入的处理 

//6. %c 使用 char 类型来替换 

String formatStr = "我的姓名是%s 年龄是%d，成绩是%.2f 性别是%c.希望大家喜欢我！"; 

String info2 = String.format(formatStr, name, age, score, gender); 

System.out.println("info2=" \+ info2); } 

}

#### StringBuffer

![image-20210720140029522](D:\myTypora\typora-pic\image-20210720140029522.png)

![image-20210720140044624](D:\myTypora\typora-pic\image-20210720140044624.png)

##### String VS StringBuffer

![image-20210720140238880](D:\myTypora\typora-pic\image-20210720140238880.png)

在String中字符串改变要么是栈中的引用直接指向字符串常量池中一个新的对象。要么就是堆中新建了一个对象，value指向字符串常量池中新的对象，然后栈中的引用指向堆中的对象。无论如何，实际上都是改变的地址。

##### String 和 StringBuffer的相互转换

###### String->StringBuffer

String str = "hello tom"; 

//方式 1 使用构造器 

//注意： 返回的才是 StringBuffer 对象，对 str 本身没有影响 

StringBuffer stringBuffer = new StringBuffer(str); 

//方式 2 使用的是 append 方法 

StringBuffer stringBuffer1 = new StringBuffer(); 

stringBuffer1 = stringBuffer1.append(str); 

###### StringBuffer \-\>String

StringBuffer stringBuffer3 = 

new StringBuffer("韩顺平教育"); 

//方式 1 使用 StringBuffer 提供的 toString 方法 

String s = stringBuffer3.toString(); 

//方式 2: 使用构造器来搞定 

String s1 = new String(stringBuffer3);

##### StringBuffer 类常见方法

![image-20210720143623562](D:\myTypora\typora-pic\image-20210720143623562.png)

![image-20210720143633130](D:\myTypora\typora-pic\image-20210720143633130.png)

![image-20210720143724051](D:\myTypora\typora-pic\image-20210720143724051.png)

插入：

![image-20210720143742009](D:\myTypora\typora-pic\image-20210720143742009.png)

![image-20210720143749902](D:\myTypora\typora-pic\image-20210720143749902.png)

##### 测试题

![image-20210720144746009](D:\myTypora\typora-pic\image-20210720144746009.png)

#### StringBuilder

![image-20210720151627639](D:\myTypora\typora-pic\image-20210720151627639.png)

##### 方法

![image-20210720152522277](D:\myTypora\typora-pic\image-20210720152522277.png)

##### String、StringBuffer、StringBuilder比较

![image-20210720152505518](D:\myTypora\typora-pic\image-20210720152505518.png)

![image-20210720153315878](D:\myTypora\typora-pic\image-20210720153315878.png)

### Math类

![image-20210720154720447](D:\myTypora\typora-pic\image-20210720154720447.png)

### Arrays类（就是数组）

#### 常用方法

![image-20210721083732001](D:\myTypora\typora-pic\image-20210721083732001.png)

定制排序，将对象根据价格从从小到大排序。

![image-20210721101054824](D:\myTypora\typora-pic\image-20210721101054824.png)

![image-20210721101103216](D:\myTypora\typora-pic\image-20210721101103216.png)

![image-20210721083737892](D:\myTypora\typora-pic\image-20210721083737892.png)

### System类

![image-20210721101335755](D:\myTypora\typora-pic\image-20210721101335755.png)

### BigInteger 和 BigDecimal 类

![image-20210721101855001](D:\myTypora\typora-pic\image-20210721101855001.png)

#### 常见方法

![image-20210721101908597](D:\myTypora\typora-pic\image-20210721101908597.png)

### 日期类

#### 第一代日期类

![image-20210721102436499](D:\myTypora\typora-pic\image-20210721102436499.png)

还可以把格式化的字符串转换成日期

#### 第二代日期类

![image-20210721102457290](D:\myTypora\typora-pic\image-20210721102457290.png)

可获得单独的年月日信息，自己可以随意组合。

#### 第三代日期类

![image-20210721102505494](D:\myTypora\typora-pic\image-20210721102505494.png)

![image-20210721102511083](D:\myTypora\typora-pic\image-20210721102511083.png)

![image-20210721105152299](D:\myTypora\typora-pic\image-20210721105152299.png)

时间戳

![image-20210721105452530](D:\myTypora\typora-pic\image-20210721105452530.png)

### 集合

![image-20210721145226081](D:\myTypora\typora-pic\image-20210721145226081.png)

#### 集合结构图

![image-20210721145239743](D:\myTypora\typora-pic\image-20210721145239743.png)

![image-20210721145243946](D:\myTypora\typora-pic\image-20210721145243946.png)

#### Collections常用方法

![image-20210721151310105](D:\myTypora\typora-pic\image-20210721151310105.png)

#### 遍历集合的Iterator迭代器

![image-20210721153115511](D:\myTypora\typora-pic\image-20210721153115511.png)

![image-20210721153128114](D:\myTypora\typora-pic\image-20210721153128114.png)

![image-20210721153141115](D:\myTypora\typora-pic\image-20210721153141115.png)

注意，如果想重新使用Ierator迭代器遍历集合，那么需要重置迭代器，让指针回到初始位置

iterator = col.iterator();//重新赋值一下就行。

#### 增强for

![image-20210721153438886](D:\myTypora\typora-pic\image-20210721153438886.png)

#### List接口

![image-20210722084040387](D:\myTypora\typora-pic\image-20210722084040387.png)

##### 方法：

![image-20210722084057241](D:\myTypora\typora-pic\image-20210722084057241.png)

##### 三种遍历方式：

![image-20210722084916045](D:\myTypora\typora-pic\image-20210722084916045.png)

##### ArrayList子类

![image-20210722092413661](D:\myTypora\typora-pic\image-20210722092413661.png)

###### ArrayList 的底层操作机制源码分析(重点，难点.)

![image-20210722093129992](D:\myTypora\typora-pic\image-20210722093129992.png)

![image-20210722095512852](D:\myTypora\typora-pic\image-20210722095512852.png)

![image-20210722095519104](D:\myTypora\typora-pic\image-20210722095519104.png)

注意：如果扩容之后的元素还是不够，则直接将数组长度扩容至需要的长度，就是上张图片第一个if语句。

jdk8和jdk16源码实现细节不同，但是扩容机制是一样的。

##### Vector 子类

![image-20210722101555902](D:\myTypora\typora-pic\image-20210722101555902.png)

###### Vector和ArrayList比较

![image-20210722101738125](D:\myTypora\typora-pic\image-20210722101738125.png)

无参构造器调用的是参数为10的有参构造器。

有参构造器和ArrayList很像。

##### LinkedList

![image-20210722102701974](D:\myTypora\typora-pic\image-20210722102701974.png)

###### LinkedList 的底层操作机制

![image-20210722110037460](D:\myTypora\typora-pic\image-20210722110037460.png)

自己debug一下追踪下源码

###### ArrayList 和 LinkedList 比较

![image-20210722110236706](D:\myTypora\typora-pic\image-20210722110236706.png)

#### Set接口

![image-20210722131728489](D:\myTypora\typora-pic\image-20210722131728489.png)

和 List 接口一样, Set 接口也是 Collection 的子接口，因此，常用方法和 Collection 接口一样. 

##### ![image-20210722131823226](D:\myTypora\typora-pic\image-20210722131823226.png)

##### HashSet

![image-20210722132832017](D:\myTypora\typora-pic\image-20210722132832017.png)

###### 底层机制（非常重要）

##### ![image-20210722153515829](D:\myTypora\typora-pic\image-20210722153515829.png)

![image-20210722171211062](D:\myTypora\typora-pic\image-20210722171211062.png)

第五步中应该会先判断是否是同个对象，如果不是同个对象再调用equals判断。

hash决定了索引的的位置

而key代表对象，比较是否是同一个对象

如果不是同一个对象调用equals方法比较，如果是同一个对象，则直接进行e = p;

![image-20210722153535747](D:\myTypora\typora-pic\image-20210722153535747.png)

关于这个临界值，并不是一定要存储在数组中，存储在链表中也算。

##### LinkedHashSet（继承了HashSet）

![image-20210722164105921](D:\myTypora\typora-pic\image-20210722164105921-16338704834075.png)

![image-20210722164119471](D:\myTypora\typora-pic\image-20210722164119471.png)

##### TreeSet

![image-20210723143928361](D:\myTypora\typora-pic\image-20210723143928361.png)

![image-20210723143938157](D:\myTypora\typora-pic\image-20210723143938157.png)

上面使用无参构造器时说错了，正确说法看下面的TreeMap中的说法。TreeSet底层是由TreeMap实现的。

下面的key是要加入的元素，t是当前遍历到的树中的对象。

如果key小于t.key那么cmp就为0，t就遍历到左子树否则遍历到右子树，如果相等那么就用Value覆盖，但由于Set中数据保存在key中Value是个常量，所以没有变化。

最终加入的key是加入到叶子节点的，符合树的规则。用中序遍历出来就是有序的。

![image-20210723143952466](D:\myTypora\typora-pic\image-20210723143952466.png)

![image-20210723144009325](D:\myTypora\typora-pic\image-20210723144009325.png)

![image-20210723144110470](D:\myTypora\typora-pic\image-20210723144110470.png)



#### Map接口

![image-20210723084435081](D:\myTypora\typora-pic\image-20210723084435081.png)

当加入key相同的元素时，只会覆盖value不会覆盖key。

所以在HashMap中key不变value如果不同则会改变

在HashSet中由于元素只存储在key中，value中存储的是常量PRESENT，所以不会有什么改变。

![image-20210723090406971](D:\myTypora\typora-pic\image-20210723090406971.png)

Keyset管理key，Values管理value，这两个又被封装成EntrySet。每一个key和value组成一个Entry

key和value实际上存储在Node类型里面的，Entry只是对于Node里面数据的引用。

##### Map常用方法

![image-20210723094141183](D:\myTypora\typora-pic\image-20210723094141183.png)

##### Map遍历方法

![image-20210723094403535](D:\myTypora\typora-pic\image-20210723094403535.png)

![image-20210723094803317](D:\myTypora\typora-pic\image-20210723094803317.png)

//第一组: 先取出 所有的 Key , 通过 Key 取出对应的 Value 

Set keyset = map.keySet(); 

![image-20210723095625150](D:\myTypora\typora-pic\image-20210723095625150.png)

![image-20210723095705685](D:\myTypora\typora-pic\image-20210723095705685.png)

![image-20210723095716684](D:\myTypora\typora-pic\image-20210723095716684-16338705098706.png)

![image-20210723095725791](D:\myTypora\typora-pic\image-20210723095725791.png)

##### HashMap底层源码和扩容机制

源码和上述HashSet一模一样，因为HashSet底层就是HashMap

![image-20210723105217166](D:\myTypora\typora-pic\image-20210723105217166.png)

![image-20210723105221302](D:\myTypora\typora-pic\image-20210723105221302.png)

##### HashTable

![image-20210723140445556](D:\myTypora\typora-pic\image-20210723140445556.png)

###### Hashtable 和 HashMap 对比

![image-20210723140842878](D:\myTypora\typora-pic\image-20210723140842878.png)

###### 子类Properties

![image-20210723141013800](D:\myTypora\typora-pic\image-20210723141013800.png)

##### TreeMap

![image-20210723150016342](D:\myTypora\typora-pic\image-20210723150016342-16338705221577.png)

**注意，TreeMap中，如果使用的是无参的构造器实际上还是会进行比较的，源码如下。它会默认调用key这个类的compareTo方法，上述例子中，key是String类，那么实际上他还是会调用String类的compareTo方法。**

![image-20210723151554865](D:\myTypora\typora-pic\image-20210723151554865.png)

如果是有参构造器那么源码如下，他调用的就是传入的匿名内部类中的compare方法了。

![image-20210723151733078](D:\myTypora\typora-pic\image-20210723151733078.png)

#### 总结\-开发中如何选择集合实现类(记住)

![image-20210723141040273](D:\myTypora\typora-pic\image-20210723141040273.png)

#### Collections工具类

![image-20210723153811794](D:\myTypora\typora-pic\image-20210723153811794.png)

![image-20210723153820834](D:\myTypora\typora-pic\image-20210723153820834.png)

### 泛型

传统方法问题：

![image-20210724100925740](D:\myTypora\typora-pic\image-20210724100925740.png)

泛型的好处：

![image-20210724100940913](D:\myTypora\typora-pic\image-20210724100940913.png)



![image-20210724103923097](D:\myTypora\typora-pic\image-20210724103923097.png)



![image-20210724103904221](D:\myTypora\typora-pic\image-20210724103904221-16338705372678.png)

![image-20210724104003304](D:\myTypora\typora-pic\image-20210724104003304-16338705396849.png)



#### 语法：

![image-20210724135902267](D:\myTypora\typora-pic\image-20210724135902267.png)

![image-20210724135909401](D:\myTypora\typora-pic\image-20210724135909401.png)

#### 细节

![image-20210724141613614](D:\myTypora\typora-pic\image-20210724141613614.png)

上面第三点解释了为什么我们平时可以在ArrayList中加入任何东西，取出来的时候要向下转型。因为Object是所有类的父类，而我们可以传入泛型指定的类型及其子类（第二点）。如下图，类中有泛型但是你并未给泛型指定特定类型，那么它默认Object类型。

![image-20210724142312529](D:\myTypora\typora-pic\image-20210724142312529.png)

#### 自定义泛型

##### 自定义泛型类

![image-20210724145642162](D:\myTypora\typora-pic\image-20210724145642162.png)

2）中比如T[] = new T[8];是不行的，因为T的类型此时都不知道，开多大空间是无法确定的。

3）中是因为静态方法在类加载的时候就被加载了，而泛型是在创建对象的时候由我们人为指定的，那么在类加载的时候静态方法中的泛型的类型并不确定。

##### 自定义泛型接口

![image-20210724150756690](D:\myTypora\typora-pic\image-20210724150756690.png)

##### 自定义泛型方法

![image-20210724151743826](D:\myTypora\typora-pic\image-20210724151743826.png)

关于第二点的例子：

Bird bird = new Bird();

bird.fly("nihao");你直接在fly形参表中输入字符串，那么泛型的E就会被确定为String，如果你输入的是20，那么E就会是Integer（自动装箱）。

泛型方法既可以使用泛型类中的泛型，也可以使用自己定义的泛型。

#### 泛型的继承和通配符

![image-20210724153413543](D:\myTypora\typora-pic\image-20210724153413543.png)

#### JUnit

![image-20210724161653014](D:\myTypora\typora-pic\image-20210724161653014.png)



#### 事件处理机制

![image-20210726141434420](D:\myTypora\typora-pic\image-20210726141434420.png)

![image-20210726141437362](D:\myTypora\typora-pic\image-20210726141437362.png)

![image-20210726141445934](D:\myTypora\typora-pic\image-20210726141445934.png)

![image-20210726141449951](D:\myTypora\typora-pic\image-20210726141449951.png)

![image-20210726141453617](D:\myTypora\typora-pic\image-20210726141453617.png)

### 多线程（基础）

#### 线程的创建与使用

![image-20210727091455649](D:\myTypora\typora-pic\image-20210727091455649.png)

##### 继承Thread

![image-20210727091500690](D:\myTypora\typora-pic\image-20210727091500690.png)



![image-20210727091513998](D:\myTypora\typora-pic\image-20210727091513998.png)

##### 实现Runnable接口

![image-20210727091912511](D:\myTypora\typora-pic\image-20210727091912511.png)

![image-20210727094157558](D:\myTypora\typora-pic\image-20210727094157558.png)

因为Runnable没有start方法，而Thread构造器的参数是Runnable接口，我们传入实现了Runnable接口的dog类，通过Thread调用start方法。然后调用start0，最后run方法根据动态绑定还是运行Dog类的run。（可看源码）

而直接继承Thread的方式可以直接继承到start方法，可以直接调用。

**继承Thread方法，是一个线程去操作一个对象。**

**实现Runnable接口，可以多个线程去操作一个对象。**

##### 两种方法的比较

![image-20210727095132884](D:\myTypora\typora-pic\image-20210727095132884.png)

#### 线程终止

![image-20210727102307551](D:\myTypora\typora-pic\image-20210727102307551.png)

![image-20210727102310788](D:\myTypora\typora-pic\image-20210727102310788.png)

#### 线程常用方法

![image-20210727102315786](D:\myTypora\typora-pic\image-20210727102315786.png)

![image-20210727102354453](D:\myTypora\typora-pic\image-20210727102354453-163387059470710.png)

##### 注意事项与细节

![image-20210727102337701](D:\myTypora\typora-pic\image-20210727102337701.png)

##### 守护线程

![image-20210727140150637](D:\myTypora\typora-pic\image-20210727140150637.png)

![image-20210727140156805](D:\myTypora\typora-pic\image-20210727140156805.png)

#### 线程的生命周期以及状态

Ready和Running统称Runnable状态。

![image-20210727141837223](D:\myTypora\typora-pic\image-20210727141837223.png)

#### 线程同步机制

![image-20210727143248677](D:\myTypora\typora-pic\image-20210727143248677.png)

![image-20210727145318091](D:\myTypora\typora-pic\image-20210727145318091.png)

##### 互斥锁

![image-20210727145608209](D:\myTypora\typora-pic\image-20210727145608209.png)

第六点是因为静态方法不属于某个对象，所有对象共同维护。

![image-20210727151009558](D:\myTypora\typora-pic\image-20210727151009558.png)

关于第三点第三部，如果是使用extends Thread方法创建线程，那么syncronized（this）就不行，因为，这种方法创建的线程操作的对象是不同的对象。可以在类中定义一个静态的对象作为属性，然后利用这个对象进行互斥操作。

##### 释放锁

![image-20210727152852387](D:\myTypora\typora-pic\image-20210727152852387.png)

以下四种情况释放锁

![image-20210727152900334](D:\myTypora\typora-pic\image-20210727152900334.png)

下面几种操作不会释放锁

![image-20210727153001731](D:\myTypora\typora-pic\image-20210727153001731.png)

### 文件

![image-20210729082630953](D:\myTypora\typora-pic\image-20210729082630953.png)

#### 常用文件操作

![image-20210729091707440](D:\myTypora\typora-pic\image-20210729091707440.png)

![image-20210729091726547](D:\myTypora\typora-pic\image-20210729091726547.png)

![image-20210729091741057](D:\myTypora\typora-pic\image-20210729091741057.png)

#### IO流原理及其分类

![image-20210729093005295](D:\myTypora\typora-pic\image-20210729093005295.png)

![image-20210729093017208](D:\myTypora\typora-pic\image-20210729093017208.png)

##### 分类

![image-20210729093033870](D:\myTypora\typora-pic\image-20210729093033870.png)

​	

#### IO流体系图

![image-20210729093215810](D:\myTypora\typora-pic\image-20210729093215810.png)

查看方法就去看官网api

在新建输出流对象时，追加模式的意思是我这个输出流的指针指向了指定文件的最后一个位置。如果不是追加模式，那么输出流的指针指向指定文件的第一个位置。非追加模式中，不是每写一次指针都会移到文件开头，在本次输出流对象关闭或者刷新之前，指针都是指向最后的，只有关闭后再创建一个非追加模式的输出流对象或者刷新以后，指针才会指向文件的开头。

#### 节点流和处理流

##### 概念

![image-20210729135753995](D:\myTypora\typora-pic\image-20210729135753995.png)

##### 一览图

![image-20210729135759008](D:\myTypora\typora-pic\image-20210729135759008.png)

处理流中的构造器的参数是抽象基类类型，可以放各种具体的节点流，其实是多态的向上转型。

##### 二者的区别和联系

![image-20210729135807795](D:\myTypora\typora-pic\image-20210729135807795.png)

##### 处理流（包装流）的优点

![image-20210729140057408](D:\myTypora\typora-pic\image-20210729140057408.png)

##### 处理流\-BufferedReader 和 BufferedWriter

![image-20210729142703459](D:\myTypora\typora-pic\image-20210729142703459.png)

##### 处理流\-BufferedInputStream 和 BufferedOutputStream

![image-20210729153132326](D:\myTypora\typora-pic\image-20210729153132326.png)

![image-20210729153138148](D:\myTypora\typora-pic\image-20210729153138148.png)

##### 对象流\-ObjectInputStream 和 ObjectOutputStream

![image-20210729153212665](D:\myTypora\typora-pic\image-20210729153212665.png)

![image-20210729160103596](D:\myTypora\typora-pic\image-20210729160103596.png)

功能：提供了对基本类型或对象类型的序列化和反序列化的方法 

ObjectOutputStream 提供 序列化功能 

ObjectInputStream 提供 反序列化功能

###### 细节

![image-20210729160151493](D:\myTypora\typora-pic\image-20210729160151493.png)

##### 转换流***

##### ![image-20210730084217070](D:\myTypora\typora-pic\image-20210730084217070.png)

##### 打印流

![image-20210730093748536](D:\myTypora\typora-pic\image-20210730093748536.png)

![image-20210730093752009](D:\myTypora\typora-pic\image-20210730093752009.png)

#### 标准输入输出流

![image-20210730084044785](D:\myTypora\typora-pic\image-20210730084044785.png)

#### Properties类

![image-20210730094729606](D:\myTypora\typora-pic\image-20210730094729606.png)

传统方法：

![image-20210730094759871](D:\myTypora\typora-pic\image-20210730094759871.png)

Properties方法

![image-20210730094820829](D:\myTypora\typora-pic\image-20210730094820829.png)

![image-20210730094824319](D:\myTypora\typora-pic\image-20210730094824319.png)

### 网络编程

#### InetAddress类

##### 相关方法

![image-20210805095050095](D:\myTypora\typora-pic\image-20210805095050095.png)

#### Socket

![image-20210805101436253](D:\myTypora\typora-pic\image-20210805101436253.png)

![image-20210805101442469](D:\myTypora\typora-pic\image-20210805101442469.png)

#### TCP网络通信编程

![image-20210805101507345](D:\myTypora\typora-pic\image-20210805101507345.png)

![image-20210805101511308](D:\myTypora\typora-pic\image-20210805101511308.png)

##### 使用字节流

发送消息后记得对Socket对象使用shutDownOutPut()函数,否则如果通信双方互相发消息，那么会陷入无限等待，因为双方都不知道对方什么时候才写完。

假如只有一方发消息，那么不使用shutDownOutPut()函数没关系，因为发送方写完之后会关闭输出流，那么接收方就会知道发送方发送完毕。

##### 使用字符流

##### 案例：

![image-20210805140415223](D:\myTypora\typora-pic\image-20210805140415223.png)

![image-20210805141159505](D:\myTypora\typora-pic\image-20210805141159505.png)

##### netStat指令

![image-20210805141626697](D:\myTypora\typora-pic\image-20210805141626697.png)

![image-20210805143053426](D:\myTypora\typora-pic\image-20210805143053426.png)

#### UDP编程

![image-20210805143921196](D:\myTypora\typora-pic\image-20210805143921196.png)

![image-20210805144609721](D:\myTypora\typora-pic\image-20210805144609721.png)

![image-20210805144618944](D:\myTypora\typora-pic\image-20210805144618944.png)

### 项目开发流程

![image-20210806093124097](D:\myTypora\typora-pic\image-20210806093124097.png)

### 反射

#### 入门应用

![image-20210809084906490](D:\myTypora\typora-pic\image-20210809084906490.png)

![image-20210809084957603](D:\myTypora\typora-pic\image-20210809084957603.png)

![image-20210809085011630](D:\myTypora\typora-pic\image-20210809085011630.png)

![image-20210809092655285](D:\myTypora\typora-pic\image-20210809092655285.png)

![image-20210809163555905](D:\myTypora\typora-pic\image-20210809163555905.png)

#### 反射原理图！！！

![image-20210809090749297](D:\myTypora\typora-pic\image-20210809090749297.png)

#### 反射可以做的事

![image-20210809091222928](D:\myTypora\typora-pic\image-20210809091222928.png)

#### 反射相关的主要类

![image-20210809091249502](D:\myTypora\typora-pic\image-20210809091249502.png)

#### 反射优点和缺点

![image-20210809091309243](D:\myTypora\typora-pic\image-20210809091309243.png)

#### 反射调用优化\-关闭访问检查

![image-20210809095656369](D:\myTypora\typora-pic\image-20210809095656369.png)

#### Class类

![image-20210809095709601](D:\myTypora\typora-pic\image-20210809095709601.png)

![image-20210809095712612](D:\myTypora\typora-pic\image-20210809095712612.png)

##### 常用获取类结构信息方法

###### 第一组: java.lang.Class 类

![image-20210809144219408](D:\myTypora\typora-pic\image-20210809144219408.png)

###### 第二组: java.lang.reflect.Field 类

![image-20210809144224243](D:\myTypora\typora-pic\image-20210809144224243.png)

###### 第三组: java.lang.reflect.Method 类

![image-20210809144229068](D:\myTypora\typora-pic\image-20210809144229068.png)

###### 第四组: java.lang.reflect.Constructor 类

![image-20210809144234596](D:\myTypora\typora-pic\image-20210809144234596.png)

##### 获取CLass类对象

![image-20210809102735226](D:\myTypora\typora-pic\image-20210809102735226.png)

![image-20210809102738382](D:\myTypora\typora-pic\image-20210809102738382.png)

![image-20210809102741076](D:\myTypora\typora-pic\image-20210809102741076.png)

##### 哪些类型有Class对象

![image-20210809140317059](D:\myTypora\typora-pic\image-20210809140317059.png)

##### 静态加载与动态加载

![image-20210809140334376](D:\myTypora\typora-pic\image-20210809140334376.png)

![image-20210809140533150](D:\myTypora\typora-pic\image-20210809140533150.png)

![image-20210809140404216](D:\myTypora\typora-pic\image-20210809140404216.png)

假如程序没有Dog类，那么编译就会报错，因为创建对象加载类是静态加载，但是没有Person类编译不会报错，因为反射加载类是动态加载，只有当你真的运行case“2”，它才会报错

##### 类加载流程

![image-20210809141044975](D:\myTypora\typora-pic\image-20210809141044975.png)



###### 加载阶段

![image-20210809143555319](D:\myTypora\typora-pic\image-20210809143555319.png)

###### 连接阶段\-验证

![image-20210809143638841](D:\myTypora\typora-pic\image-20210809143638841.png)

###### 连接阶段\-准备

![image-20210809143650773](D:\myTypora\typora-pic\image-20210809143650773.png)

![image-20210809143708148](D:\myTypora\typora-pic\image-20210809143708148.png)

###### 连接阶段\-解析

![image-20210809143712625](D:\myTypora\typora-pic\image-20210809143712625.png)

###### Initialization（初始化)

![image-20210809143717793](D:\myTypora\typora-pic\image-20210809143717793.png)

#### 通过反射创建对象

![image-20210809154155423](D:\myTypora\typora-pic\image-20210809154155423.png)

#### 通过反射访问类中的成员变量

![image-20210809155405008](D:\myTypora\typora-pic\image-20210809155405008.png)

#### 通过反射访问类中的方法

![image-20210809155411881](D:\myTypora\typora-pic\image-20210809155411881.png)

### mysql

#### 命令行连接到mysql

![image-20210810100111881](D:\myTypora\typora-pic\image-20210810100111881.png)

![image-20210810100116655](D:\myTypora\typora-pic\image-20210810100116655.png)

#### mysql三层结构

![image-20210810141618465](D:\myTypora\typora-pic\image-20210810141618465.png)

#### SQL语句分类

![image-20210810150617416](D:\myTypora\typora-pic\image-20210810150617416.png)

#### 备份恢复数据库

![image-20210810151111708](D:\myTypora\typora-pic\image-20210810151111708.png)

备份的sql文件中实际上是sql语句，备份就是将数据库存储成sql语句，在恢复的时候执行这些sql语句。

#### 备份恢复数据库的表

![image-20210810151415657](D:\myTypora\typora-pic\image-20210810151415657.png)

#### 常用列类型

![image-20210811085015781](D:\myTypora\typora-pic\image-20210811085015781.png)

#####  数值型

![image-20210811092850380](D:\myTypora\typora-pic\image-20210811092850380.png)

![image-20210811092901974](D:\myTypora\typora-pic\image-20210811092901974.png)

数值型bit的使用

![image-20210811092909569](D:\myTypora\typora-pic\image-20210811092909569.png)

数值型(小数)的基本使用

![image-20210811093021534](D:\myTypora\typora-pic\image-20210811093021534.png)

#### 字符串型

![image-20210811093036241](D:\myTypora\typora-pic\image-20210811093036241.png)

##### 字符串使用细节

![image-20210811093118401](D:\myTypora\typora-pic\image-20210811093118401.png)

![image-20210811093120914](D:\myTypora\typora-pic\image-20210811093120914.png)

![image-20210811093123712](D:\myTypora\typora-pic\image-20210811093123712.png)

![image-20210811093127253](D:\myTypora\typora-pic\image-20210811093127253.png)

##### 日期类型

![image-20210811100419120](D:\myTypora\typora-pic\image-20210811100419120.png)

#### 表的创建删除和修改

##### 创建

![image-20210811145330401](D:\myTypora\typora-pic\image-20210811145330401.png)

![image-20210811145338994](D:\myTypora\typora-pic\image-20210811145338994.png)

##### 删除

DROP TABLE emp

##### 修改

![image-20210811145516547](D:\myTypora\typora-pic\image-20210811145516547.png)

#### INSERTE语句

![image-20210811143917837](D:\myTypora\typora-pic\image-20210811143917837.png)

第七点，就是说你如果没有给所有元素赋值，那么你必须在前面写字段名称。

#### UPDATE语句

![image-20210811144739379](D:\myTypora\typora-pic\image-20210811144739379.png)

![image-20210811144802644](D:\myTypora\typora-pic\image-20210811144802644.png)

#### DELETE语句

![image-20210811145015861](D:\myTypora\typora-pic\image-20210811145015861.png)

![image-20210811145025510](D:\myTypora\typora-pic\image-20210811145025510.png)

#### SELECT语句***

FROM后面的一些语句表示是将原表筛选出其中的一部分，然后select后面from前面的语句则是对筛选出来的这一部分进行挑选并呈现。

![image-20210811150747758](D:\myTypora\typora-pic\image-20210811150747758.png)

![image-20210811150759195](D:\myTypora\typora-pic\image-20210811150759195.png)

##### 使用表达式对查询的列进行运算

![image-20210811150856228](D:\myTypora\typora-pic\image-20210811150856228.png)

![image-20210811150933125](D:\myTypora\typora-pic\image-20210811150933125.png)

##### 在 select 语句中可使用 as 语句

![image-20210811150859689](D:\myTypora\typora-pic\image-20210811150859689.png)



##### 在 where 子句中经常使用的运算符

![image-20210811153302194](D:\myTypora\typora-pic\image-20210811153302194.png)

##### 使用 order by 子句排序查询结果

![image-20210811153342161](D:\myTypora\typora-pic\image-20210811153342161-163387077421611.png)

![image-20210811153346888](D:\myTypora\typora-pic\image-20210811153346888.png)

#### 合计/统计函数

##### count

![image-20210811153952702](D:\myTypora\typora-pic\image-20210811153952702.png)

##### sum

![image-20210811154227896](D:\myTypora\typora-pic\image-20210811154227896.png)

##### avg

![image-20210811154401379](D:\myTypora\typora-pic\image-20210811154401379.png)

##### max/min

![image-20210811154441532](D:\myTypora\typora-pic\image-20210811154441532.png)

##### group by

![image-20210812084008523](D:\myTypora\typora-pic\image-20210812084008523.png)

![image-20210812084055498](D:\myTypora\typora-pic\image-20210812084055498.png)

groupby意味着对原来的表按照某些列进行分组，此时select后面操作的对象就是那**一个个分组**。比如下面这个例子：SELECT COUNT(*) , job

​				FROM EMP

​				GROUP BY job

此时的count(\*)代表对每个分组进行统计，这个\*代表的是每个分组中的所有元素，而不是整个表。

#### 字符串函数

![image-20210812090056263](D:\myTypora\typora-pic\image-20210812090056263.png)

![image-20210812090113068](D:\myTypora\typora-pic\image-20210812090113068.png)

#### 数学相关函数

![image-20210812091039786](D:\myTypora\typora-pic\image-20210812091039786.png)

日期时间相关函数

![image-20210812093035872](D:\myTypora\typora-pic\image-20210812093035872.png)

![image-20210812093023337](D:\myTypora\typora-pic\image-20210812093023337.png)

![image-20210812093823576](D:\myTypora\typora-pic\image-20210812093823576-163387079594912.png)

#### 加密和系统函数

![image-20210812095823324](D:\myTypora\typora-pic\image-20210812095823324.png)

#### 流程控制函数

![image-20210812102435737](D:\myTypora\typora-pic\image-20210812102435737.png)

![image-20210812102450940](D:\myTypora\typora-pic\image-20210812102450940.png)

#### 分页查询

![image-20210812141918254](D:\myTypora\typora-pic\image-20210812141918254.png)

#### 分组统计

顺序是groupby  having  orderby  limit

![image-20210812144408243](D:\myTypora\typora-pic\image-20210812144408243.png)

看看这篇文章：https://blog.csdn.net/zj20142213/article/details/81073428

所以groupby之后，在select中，要么只能显示groupby后面的元素，要么在select中使用聚合函数。

##### 对一列进行groupby

![image-20210813105032960](D:\myTypora\typora-pic\image-20210813105032960.png)

##### 对多列进行groupby

![image-20210813105057673](D:\myTypora\typora-pic\image-20210813105057673.png)

##### 常见聚合函数

![image-20210813105222803](D:\myTypora\typora-pic\image-20210813105222803.png)

#### 多表查询***

老韩小技巧：多表查询的条件不能少于 表的个数-1, 否则会出现笛卡尔集

多表查询如果没有WHERE进行筛选，那么select出来的结果将会是全部元素的笛卡尔积。因此，where的筛选是在此基础上的筛选。

##### 自连接

![image-20210813085709397](D:\myTypora\typora-pic\image-20210813085709397.png)

![image-20210813090443723](D:\myTypora\typora-pic\image-20210813090443723.png)

#####  子查询

子查询是指嵌入在其它 sql 语句中的 select 语句,也叫嵌套查询

##### 单行子查询

![image-20210813092037387](D:\myTypora\typora-pic\image-20210813092037387.png)

##### 多行子查询

![image-20210813092043773](D:\myTypora\typora-pic\image-20210813092043773.png)

##### 多行子查询中的all和any

![image-20210813093405878](D:\myTypora\typora-pic\image-20210813093405878.png)

![image-20210813093504225](D:\myTypora\typora-pic\image-20210813093504225.png)

##### 多列子查询

![image-20210813134730840](D:\myTypora\typora-pic\image-20210813134730840.png)

##### 子查询当临时表

![image-20210813093051754](D:\myTypora\typora-pic\image-20210813093051754.png)

![image-20210813093058813](D:\myTypora\typora-pic\image-20210813093058813.png)

#### 表复制

![image-20210813135410692](D:\myTypora\typora-pic\image-20210813135410692.png)

![image-20210813135427893](D:\myTypora\typora-pic\image-20210813135427893.png)

\-- 如何删除掉一张表重复记录？

![image-20210813140136720](D:\myTypora\typora-pic\image-20210813140136720.png)

#### 合并查询

![image-20210813140533617](D:\myTypora\typora-pic\image-20210813140533617.png)

![image-20210813140536471](D:\myTypora\typora-pic\image-20210813140536471.png)

#### 外连接

![image-20210813143121348](D:\myTypora\typora-pic\image-20210813143121348.png)

![image-20210813143149247](D:\myTypora\typora-pic\image-20210813143149247.png)

![image-20210813143233239](D:\myTypora\typora-pic\image-20210813143233239.png)

#### mysql约束

![image-20210814084413102](D:\myTypora\typora-pic\image-20210814084413102.png)

##### 主键

![image-20210814084428028](D:\myTypora\typora-pic\image-20210814084428028.png)

##### not null

![image-20210814085022691](D:\myTypora\typora-pic\image-20210814085022691.png)

##### unique

![image-20210814085033496](D:\myTypora\typora-pic\image-20210814085033496.png)

![image-20210814085036560](D:\myTypora\typora-pic\image-20210814085036560.png)

##### 外键

![image-20210814090729710](D:\myTypora\typora-pic\image-20210814090729710.png)

![image-20210814090739100](D:\myTypora\typora-pic\image-20210814090739100.png)

##### check

![image-20210814091429850](D:\myTypora\typora-pic\image-20210814091429850-163387086100113.png)

#### 自增长

![image-20210814093254748](D:\myTypora\typora-pic\image-20210814093254748.png)

![image-20210814093256805](D:\myTypora\typora-pic\image-20210814093256805.png)

#### 索引

![image-20210814135710663](D:\myTypora\typora-pic\image-20210814135710663.png)

##### 索引的原理

![image-20210814140650852](D:\myTypora\typora-pic\image-20210814140650852.png)

##### 索引的类型

![image-20210814141708428](D:\myTypora\typora-pic\image-20210814141708428.png)

##### 索引的使用

![image-20210814142450292](D:\myTypora\typora-pic\image-20210814142450292.png)

![image-20210814142457312](D:\myTypora\typora-pic\image-20210814142457312.png)

![image-20210814142516736](D:\myTypora\typora-pic\image-20210814142516736.png)

![image-20210814142538983](D:\myTypora\typora-pic\image-20210814142538983.png)

![image-20210814142609950](D:\myTypora\typora-pic\image-20210814142609950.png)

![image-20210814142711854](D:\myTypora\typora-pic\image-20210814142711854.png)![image-20210814142717640](D:\myTypora\typora-pic\image-20210814142717640.png)

##### 索引小结

![image-20210814143649735](D:\myTypora\typora-pic\image-20210814143649735.png)

#### 事务

![image-20210814150531985](D:\myTypora\typora-pic\image-20210814150531985.png)

![image-20210814150552974](D:\myTypora\typora-pic\image-20210814150552974.png)

##### 事务的基本操作

![image-20210814150612439](D:\myTypora\typora-pic\image-20210814150612439.png)

![image-20210814151520983](D:\myTypora\typora-pic\image-20210814151520983.png)

![image-20210814151531457](D:\myTypora\typora-pic\image-20210814151531457.png)

###### 回退事务

![image-20210814151607028](D:\myTypora\typora-pic\image-20210814151607028.png)

###### 提交事务

![image-20210814151610978](D:\myTypora\typora-pic\image-20210814151610978.png)

##### 事务细节

![image-20210814151618382](D:\myTypora\typora-pic\image-20210814151618382.png)

##### 隔离级别

1.隔离级别首先和事务有关，离开了事务就不要谈隔离级别。

![image-20210816082051977](D:\myTypora\typora-pic\image-20210816082051977.png)

![image-20210816082100584](D:\myTypora\typora-pic\image-20210816082100584.png)

![image-20210816082112077](D:\myTypora\typora-pic\image-20210816082112077-163387090325714.png)

###### 设置事务隔离级别的操作

![image-20210816083141938](D:\myTypora\typora-pic\image-20210816083141938.png)

##### ACID

![image-20210816092614564](D:\myTypora\typora-pic\image-20210816092614564.png)

#### 表类型和存储引擎

![image-20210816093614743](D:\myTypora\typora-pic\image-20210816093614743.png)

##### 主要的存储引擎/表类型特点

![image-20210816093636248](D:\myTypora\typora-pic\image-20210816093636248.png)

##### 细节说明

![image-20210816093651396](D:\myTypora\typora-pic\image-20210816093651396.png)

##### 如何选择表的引擎

![image-20210816094821015](D:\myTypora\typora-pic\image-20210816094821015.png)

##### 修改表的引擎

![image-20210816094836598](D:\myTypora\typora-pic\image-20210816094836598.png)

#### 视图

![image-20210816140250393](D:\myTypora\typora-pic\image-20210816140250393.png)

##### 概念

![image-20210816140258862](D:\myTypora\typora-pic\image-20210816140258862.png)

![image-20210816140307194](D:\myTypora\typora-pic\image-20210816140307194.png)

##### 视图的使用

![image-20210816141416810](D:\myTypora\typora-pic\image-20210816141416810.png)

##### 视图的细节

![image-20210816141540265](D:\myTypora\typora-pic\image-20210816141540265.png)

![image-20210816141456356](D:\myTypora\typora-pic\image-20210816141456356.png)

##### 视图最佳实践

![image-20210816141552782](D:\myTypora\typora-pic\image-20210816141552782.png)

#### mysql管理

##### 用户管理

![image-20210816145013398](D:\myTypora\typora-pic\image-20210816145013398.png)

###### 创建用户

![image-20210816145026526](D:\myTypora\typora-pic\image-20210816145026526.png)

###### 删除用户

![image-20210816145033556](D:\myTypora\typora-pic\image-20210816145033556.png)

###### 修改密码

![image-20210816145043980](D:\myTypora\typora-pic\image-20210816145043980.png)

##### 权限管理

![image-20210816150818161](D:\myTypora\typora-pic\image-20210816150818161.png)

###### 给用户授权

![image-20210816150849375](D:\myTypora\typora-pic\image-20210816150849375.png)

###### 回收用户授权

![image-20210816150908646](D:\myTypora\typora-pic\image-20210816150908646.png)

###### 权限生效指令

![image-20210816150927615](D:\myTypora\typora-pic\image-20210816150927615.png)

##### 细节说明

![image-20210816151010343](D:\myTypora\typora-pic\image-20210816151010343.png)

### JDBC

#### 原理

![image-20210818090229345](D:\myTypora\typora-pic\image-20210818090229345.png)

![image-20210818090231922](D:\myTypora\typora-pic\image-20210818090231922.png)

#### 好处

![image-20210818091145945](D:\myTypora\typora-pic\image-20210818091145945.png)

![image-20210818091149028](D:\myTypora\typora-pic\image-20210818091149028.png)

#### API大体浏览

![image-20210818094909364](D:\myTypora\typora-pic\image-20210818094909364.png)

#### 快速入门-使用步骤

![image-20210818094949227](D:\myTypora\typora-pic\image-20210818094949227.png)

![image-20210818095009856](D:\myTypora\typora-pic\image-20210818095009856.png)

![image-20210818095019988](D:\myTypora\typora-pic\image-20210818095019988.png)

![image-20210818095030679](D:\myTypora\typora-pic\image-20210818095030679.png)

#### 连接数据库的五种方式

##### 方式一：

![image-20210818103251993](D:\myTypora\typora-pic\image-20210818103251993.png)

##### 方式二：

![image-20210818103255928](D:\myTypora\typora-pic\image-20210818103255928.png)

##### 方式三：

![image-20210818103300593](D:\myTypora\typora-pic\image-20210818103300593.png)

##### 方式四：

![image-20210818103304358](D:\myTypora\typora-pic\image-20210818103304358.png)

##### 方式五：（推荐使用）

![image-20210818103308470](D:\myTypora\typora-pic\image-20210818103308470.png)

#### ResultSet（结果集）

![image-20210818140146200](D:\myTypora\typora-pic\image-20210818140146200.png)

![image-20210818140151589](D:\myTypora\typora-pic\image-20210818140151589.png)

##### 底层源码

![image-20210818140242700](D:\myTypora\typora-pic\image-20210818140242700.png)

#### 应用实例

![image-20210818140413023](D:\myTypora\typora-pic\image-20210818140413023.png)

![image-20210818140421999](D:\myTypora\typora-pic\image-20210818140421999.png)

![image-20210818140433940](D:\myTypora\typora-pic\image-20210818140433940.png)

![image-20210818140442371](D:\myTypora\typora-pic\image-20210818140442371.png)

![image-20210818140450375](D:\myTypora\typora-pic\image-20210818140450375.png)

#### Statement

![image-20210818141339057](D:\myTypora\typora-pic\image-20210818141339057.png)

![image-20210818141412969](D:\myTypora\typora-pic\image-20210818141412969.png)

由于'1' = '1'永远成立，那么总能查询出一个用户。如果是登录程序的话那么就登陆进去了。

#### PreparedStatement

![image-20210818143446528](D:\myTypora\typora-pic\image-20210818143446528.png)

##### 预处理好处

![image-20210818143500566](D:\myTypora\typora-pic\image-20210818143500566.png)

##### 应用实例

![image-20210818143527044](D:\myTypora\typora-pic\image-20210818143527044.png)

![image-20210818143535533](D:\myTypora\typora-pic\image-20210818143535533.png)

![image-20210818143849168](D:\myTypora\typora-pic\image-20210818143849168.png)

![image-20210818143810594](D:\myTypora\typora-pic\image-20210818143810594.png)

![image-20210818143816790](D:\myTypora\typora-pic\image-20210818143816790.png)

注意4中executeUpdate的参数不要再写sql这个和Statement不同。前面已经预处理过了。

#### API小结

![image-20210818145606306](D:\myTypora\typora-pic\image-20210818145606306.png)

![image-20210818145610989](D:\myTypora\typora-pic\image-20210818145610989.png)

#### JDBCUtils

可以把对数据库的连接以及释放操作单独制作一个Utils工具类

#### JDBC控制事务

![image-20210819092436649](D:\myTypora\typora-pic\image-20210819092436649.png)

![image-20210819092508203](D:\myTypora\typora-pic\image-20210819092508203.png)

![image-20210819092518543](D:\myTypora\typora-pic\image-20210819092518543.png)

![image-20210819092535629](D:\myTypora\typora-pic\image-20210819092535629.png)

![image-20210819092545188](D:\myTypora\typora-pic\image-20210819092545188.png)

![image-20210819092557278](D:\myTypora\typora-pic\image-20210819092557278.png)

#### 批处理

![image-20210819094842335](D:\myTypora\typora-pic\image-20210819094842335.png)

![image-20210819094849223](D:\myTypora\typora-pic\image-20210819094849223.png)

![image-20210819094856220](D:\myTypora\typora-pic\image-20210819094856220.png)

![image-20210819094941701](D:\myTypora\typora-pic\image-20210819094941701.png)

#### 数据库连接池

##### 传统连接方式

![image-20210819142514232](D:\myTypora\typora-pic\image-20210819142514232.png)

##### 连接池方式

![image-20210819142708272](D:\myTypora\typora-pic\image-20210819142708272.png)

![image-20210819142623119](D:\myTypora\typora-pic\image-20210819142623119.png)

c3p0和Druid的使用看视频或者老师笔记。

#### ApDBUtils

##### 土方法解决这三个问题。

![image-20210820091116264](D:\myTypora\typora-pic\image-20210820091116264.png)

![image-20210820091119484](D:\myTypora\typora-pic\image-20210820091119484.png)

##### ApDBUtils简介

![image-20210820093919360](D:\myTypora\typora-pic\image-20210820093919360.png)

##### 应用实例（Druid + ApDBUtils 完成查找操作）

###### 返回结果是多行

![image-20210820094000187](D:\myTypora\typora-pic\image-20210820094000187.png)

![image-20210820094031744](D:\myTypora\typora-pic\image-20210820094031744.png)

![image-20210820094043321](D:\myTypora\typora-pic\image-20210820094043321.png)

![image-20210820094122688](D:\myTypora\typora-pic\image-20210820094122688.png)

![image-20210820094135285](D:\myTypora\typora-pic\image-20210820094135285.png)

![image-20210820094150952](D:\myTypora\typora-pic\image-20210820094150952.png)

![image-20210820094159136](D:\myTypora\typora-pic\image-20210820094159136.png)

![image-20210820094304297](D:\myTypora\typora-pic\image-20210820094304297.png)

###### 返回结果是单行

![image-20210820095449184](D:\myTypora\typora-pic\image-20210820095449184.png)

![image-20210820095459415](D:\myTypora\typora-pic\image-20210820095459415.png)

###### 返回结果是单行单列

![image-20210820095119846](D:\myTypora\typora-pic\image-20210820095119846.png)

![image-20210820095132107](D:\myTypora\typora-pic\image-20210820095132107.png)

##### 应用实例（Druid + ApDBUtils 完成增删改操作）

![image-20210820095941871](D:\myTypora\typora-pic\image-20210820095941871.png)

![image-20210820095906755](D:\myTypora\typora-pic\image-20210820095906755.png)

#### BasciDAO

![image-20210820142754724](D:\myTypora\typora-pic\image-20210820142754724.png)

![image-20210820142803583](D:\myTypora\typora-pic\image-20210820142803583.png)

![image-20210820142807226](D:\myTypora\typora-pic\image-20210820142807226.png)

做项目是从下往上分析，具体看满汉楼系统制作流程。

##### 基本说明

![image-20210820142828170](D:\myTypora\typora-pic\image-20210820142828170.png)

##### 应用实例：

![image-20210820142838261](D:\myTypora\typora-pic\image-20210820142838261.png)

具体设计看视频
