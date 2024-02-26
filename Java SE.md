

# Java SE

------

[TOC]

##  部分基础细点

**头文件**

>  **`import  java.util.*;`**
>
> 1. java程序本质是class文件在jvm虚拟机运行；
>
> 2. **并且注意修改了源文件，必须生成新class文件，才能生效**
>
> 3. 在编译过程中，每一个class（即类）都对应一个“.class”
>
> 4. 转义字符中需要注意的是\r回车，其意思在当前行回到行首重新输入（而非换行）
>
> 5. 定义long变量时，数字后加 ‘l'或者'L'，定义float时，加“f" 或者"F"
>
> 6. 浮点常量表示可以没有0，必须有小数点，即（.512 =  0.512）
>
> 7. 浮点数使用陷阱：（2.7和8.1/3），第二个输出的是接近2.7的一个小数
>
> 8. 字符类型可以直接存放一个数字，`char c = 97;`是正确的，并且输出时，输出的也是97所对应的Unicode对应字符。
>
> 9. 在java中的布尔类型（**boolean**），**只能用布尔类型夹在while。if等括号内，不能像c语言一样用int型代替**
>
> 10. 赋值和运算时可自动转更高精度![image-20230405164654236](https://s2.loli.net/2023/10/15/glno9D6OcRYSi8F.png)
>
> 11. java中的逻辑异或： a^b,  同真同假为false，a b不同为真
>
>     短路（&&||）和逻辑（&|）与或的区别：短路只要判断出就不会往后运行了，而逻辑左右都会执行
>
> 12. 位运算
>
>     ![image-20230405164707590](https://s2.loli.net/2023/10/15/UdOCSRbuoZ6l3Es.png)
>
> 13. java中的 printf
>
> 14. **数组**
>
>     数组的建立    `int a[] = new int  [size];`也可以分开写，先声明，再让 a= new ......;(二维数组多加一个[])
>
>     数组建立后，未赋值的话，自动赋为0（布尔类型默认为false)且对数组元素赋值时，只有符合精度兼容才不会报错，即低精度转高精度
>
> 15. **赋值**：在**基本数据类型的相互赋值是值拷贝**，修改赋过值的变量不会改变赋值变量的值，但是**数组（引用类型）与数组之间的赋值通常是引用传递，是地址拷贝，**赋值是会改变原数组的值
>
> 16. ![image-20230405164722100](https://s2.loli.net/2023/10/15/LmXJOqHUePkZcuE.png)
>
>     
>

------

------

------

## 包装类（Wrapper）

<u>**对应八种数据类型的引用类型，可调用类中的方法**</u>

<img src="https://s2.loli.net/2023/10/15/W6JO8UPR7b9jDKt.png" alt="image-20230407102856873" style="zoom: 50%;" />

------

### 包装类和基本数据类型的转换

***装箱： 基本类型->包装类型，拆箱反之**

tips：jdk5之后会自动装箱和拆箱，底层会自动调用 **<u>Integer.valueOf() 和 intValue()</u>**  

##### 包装类和String的转换

<img src="https://s2.loli.net/2023/10/15/9QMBWFduYhqs8OZ.png" alt="image-20230407104646717" style="zoom:50%;" />

<img src="https://s2.loli.net/2023/10/15/CAqk2zFQLVZjIfp.png" alt="image-20230407104934998" style="zoom:50%;" />

------

### Integer类

*①**赋值范围在（-128,127）的话直接赋值，不在的话则会调用new Integer。**

<img src="https://s2.loli.net/2023/10/15/h7NYbJAy3E1dBqa.png" alt="image-20230407111441204" style="zoom:50%;" />

------

### String类

##### String基本剖析

①**字符串的一个字符（Unicode编码）不论字母还是汉字都占两个字节**

<img src="https://s2.loli.net/2023/10/15/2fnzVDjYuc9RGyQ.png" alt="image-20230408145014816" style="zoom: 33%;" />

②看源码得知，底层里边的字符串是**<u>final byte[]</u>**，且**<u>其在堆内的内存空间地址</u>不可更改（final）**

![image-20230408144536566](https://s2.loli.net/2023/10/15/4XpodUt2ysqSa5u.png)

③<img src="https://s2.loli.net/2023/10/15/9LUdMS3ECn6tbly.png" alt="image-20230408150532348" style="zoom:50%;" />

④

![image-20230408152214570](https://s2.loli.net/2023/10/15/LPqrxAkYnWa1TgK.png)

<img src="https://s2.loli.net/2023/10/15/xdnwXNfePqy12pV.png" alt="image-20230408152314191" style="zoom:50%;" />

##### *String常用方法

> `str.intern`  	**返回str在常量池中的地址**
>
> `equals`  	**判断内容是否相等**
>
> *`indexOf`和`lastIndexOf` 	返回**字符串**在字符串第一次和最后一次出现的索引，**没有则返回-1**
>
> *`substring` 	**<u>返回</u>截取指定范围(0，n-1)的子串**
>
> `trim` 	**<u>返回</u>去前后空格后的字符串**
>
> `toUpperCase和toLowerCase` 	**全变成大写或小写**
>
> `concat`	 <u>返回</u>**拼接字符串,可以.concat().concat()**///或者直接用 “+”
>
> `replace("A","B")`      **<u>返回</u>把字符串全部的A改成B的形式，可赋给其他字符串，但对原字符串无任何影响**
>
> *`spilt(",")` 	   **以引号内为分割线分割，返回一个<u>字符串数组</u>**
>
> `toCharArray` 	 **<u>返回</u>字符数组char[]**
>
> `compareTo`			**先判断长度的大小，返回值是前减后的值**
>
> `format`		**当printf用**
>
> `.getBytes()	`	**转成字节数组（IO流要用）**
>
> `endWith()`	返回波尔变量判断是否以某字符串为结尾

- tips：标记返回的东西说明**不会再原串上进行修改**，需要在前边加上**str=**

*String改变串内容操作，是**<u>产生一个新的字符串，然后再指向它</u>**，**如果多次执行这类操作，就会导致大量副本存留在内存，降低效率，影响程序性能**。所以我们如果要对字符串进行多次修改，不要使用String

------

### *StringBuffer类

①StringBuffer里的底层**字符数组不是final类型**了，因此**存放在堆中**（final修饰的变量在常量池中）



<img src="https://s2.loli.net/2023/10/15/JClDpPO7bFge9Wc.png" alt="image-20230408161457410" style="zoom: 33%;" />

##### String和StringBuffer的相互转换

![image-20230408162555337](https://s2.loli.net/2023/10/15/v7uqy8NP2QbOwEH.png)

##### StringBuffer方法

> `append()`  	**添加括号内元素**//可添加数字和小数
>
> `delete（start，end）`   **原地对其删除（start，end-1）的元素**					
>
> `replace(start，end，“A”)`	**将start到end的东西改成“A"**
>
> `indexOf`	**同上String**
>
> *`insert(index,"A")`    **在index插入字符串A，原元素后移**
>
> *`reverse()`		**原字符串全部翻转**

**tips:append一个空字符串（null），结果竟是原字符串后边加了null**

------

### *StringBuilder类	

<img src="https://s2.loli.net/2023/10/15/XVuYe3f6sBwEWPr.png" alt="image-20230409131100536" style="zoom: 50%;" />

##### *<u>StringBuilder和StringBuffer的方法一样，均兼容，同上</u>

在单线程情况下使用StringBuilder<img src="https://s2.loli.net/2023/10/15/d7K9aJVUhzwis6T.png" alt="image-20230409130854273" style="zoom:33%;" />

------

### **三种字符串类的优劣

<img src="https://s2.loli.net/2023/10/15/gIVzdfuDmr5UsYj.png" alt="image-20230409132711538" style="zoom:50%;" />



------

### *Math类常用方法

> `ceil`	**向上取整**
>
> `floor`	**向下取整**
>
> `round`	**四舍五入**
>
> `random`	**随机数**  
>
> *求(a,b)的随机整数：**`(int)(a+Math.random()*(b-a))`**

------

### *Arrays常用方法

> `Arrays.toString`	**返回数组的字符串形式 ：[1,2,3,4,5]**
>
> *`Arrays.binarySearch()`	**二分查找一个key，<u>未找到</u>或<u>数组无序</u>返回-1**
>
> `Arrays.copyOf(a,n)`	**返回一个数组，拷贝a中前n个元素，如果拷贝多了会拷贝null**
>
> *`Arrays.fill(a,n)`	**把a中<u>所有元素</u>都换成n**
>
> `equals`     **返回<u>布尔类型</u>，判断内容是否<u>完全一致</u>**
>
> `asList` 	**转成List数据集合**
>
> `Arrays.copyOfRange`	**将数组拷贝至另外一个数组**

<img src="https://s2.loli.net/2023/10/15/XEImf2zWaFPB5Op.png" alt="image-20230409142723261" style="zoom:50%;" />

<img src="https://s2.loli.net/2023/10/15/sIncepmA6LxwGUE.png" alt="image-20230409145316376" style="zoom:50%;" />





------

### System类

> `gc()` **手动调用垃圾回收器finalize**
>
> `currentTimeMillis()`  **返回当前时间**-毫秒-(long)
>
> `exit()`	**结束程序，返回括号内数字**
>
> 



------

### 日期类

#### Date类

> `Date date = new Date();`	**获取当前时间**

#### Calendar类

> `Calendar c = Calendar.getInstance();`	**创建日历类对象**
>
> 

<img src="https://s2.loli.net/2023/10/15/WqYISLCTRgeXojU.png" alt="image-20230409154712763" style="zoom:50%;" />

#### LocalDateTimel类

> `LocalDateTime.now().var`			获取时间

<img src="https://s2.loli.net/2023/10/15/73u4gFyx69lHesC.png" alt="image-20230409155805887" style="zoom:50%;" />

------

### Random类

```java
Random r = new Random();
int num = r.nextInt(n);
//参数 n 代表指定范围的数字[0,n)
int num = r.nextInt();
//生成int范围内的数字（long同理）
float l = r.nextFloat();
//生成[0,1]之间的小数(double同理)

```

#### 和Math.random()的区别

> random.nextInt() 为 java.util.Random类中的方法；
>
> Math.random() 为 java.lang.Math 类中的静态方法。
>
> Math.random() 线程安全，多线程环境能被调用；
>
> 如无特殊需求，则使用(int)(Math.random()*n)的方式生成随机数即可。



------

### 正则表达式

> 正则表达式即**正确规则的表达式**，通常用来检测字符串是否符合某规则、根据某规则切分字符串或替换符合规则的文本 

####  常用方法

> ![image-20230417193706615](https://s2.loli.net/2023/10/15/zP2KOYrS8pRuxeb.png)

#### 常用正则表达式

> ![image-20230417193812837](https://s2.loli.net/2023/10/15/dpqHzONxhUFIAsm.png)

#### 语法规则

> 规则：**[abc]** 
> 含义：代表的是字符 a、b 或 c 
> 例如：匹配规则为"[abc]"，那么需要匹配的内容就是字符 a，或者字符 b，或字符 c 的一个 
>
> 规则：**[abc]** 
> 含义：代表的是字符 a、b 或 c 
> 例如：匹配规则为"[abc]"，那么需要匹配的内容就是字符 a，或者字符 b，或字符 c 的一个 
>
> 规则：**[a-zA-Z]** 
> 含义：代表的是 a 到 z 或 A 到 Z，两头的字母包括在内 
> 例如：匹配规则为"[a-zA-Z]"，那么需要匹配的是一个大写或者小写字母
>
> 规则：**[a-zA-Z_0-9]** 
> 含义：代表的字母或者数字或者下划线(即单词字符) 
> 例如：匹配规则为" [a-zA-Z_0-9] "，那么需要匹配的是一个字母或者是一个数字或一个下滑线
>
> 规则：**.** 
> 含义：代表的是任何字符 
> 例如：匹配规则为" . "，那么需要匹配的是一个任意字符。 

#### 边界匹配器

> 边界匹配器：^ 
> 含义：代表以某些内容开头 
>
> 边界匹配器：$ 
> 含义：代表以某些内容结尾 

#### 数量词

> 数量词：X? 
> 含义：代表的是 X 出现 0~1 次 
> 例如：匹配规则为"a?"，那么需要匹配的内容是一个字符 a，或者一个 a 都没有 
>
> 数量词：X* 
> 含义：代表的是 X 出现 次数≥0 
> 例如：匹配规则为"a*"，那么需要匹配的内容是多个字符 a，或者一个 a 都没有 
>
> 数量词：X* 
> 含义：代表的是 X 出现 次数≥0 
> 例如：匹配规则为"a*"，那么需要匹配的内容是多个字符 a，或者一个 a 都没有 
>
> 数量词：X{n} 
> 含义：代表的是 X 出现 次数= n 
> 例如：匹配规则为"a{3}"，那么需要匹配的内容是 3 个字符 a 
>
> 数量词：X{n,} 
> 含义：代表的是 X 出现 至少 n 次 
> 例如：匹配规则为"a{3, }"，那么需要匹配的内容是最少有 3 个字符 a 
>
> 数量词：X{n,m} 
> 含义：代表的是 X 出现至少 n 次，但是不超过 m 次 
> 例如：匹配规则为"a{5,8}"，那么需要匹配的内容是有 5 个字符 a 到 8 个字符 a 之间 

#### 逻辑运算符

> 逻辑运算符：XY 
> 含义：代表的是 X 后紧跟着 Y 
> 例如：匹配规则为"ab"，那么需要匹配的字符串内容就是 ”ab” 
>
> 逻辑运算符：X|Y 
> 含义：代表的是 X 或 Y 
> 例如：匹配规则为"a|b"，那么需要匹配的字符串内容就是 ”a”或”b” 
>



------

### Pattern类和Matcher类

> Pattern类用于创建一个正则表达式的模式，而Matcher类用于在给定的字符串中匹配模式。通常我们会先使用Pattern.compile()方法创建一个模式对象，然后使用Matcher.matches()或Matcher.find()方法来查找匹配项













------

------

------

------

## 面向对象编程

### 类与对象

![image-20230405164817736](https://s2.loli.net/2023/10/15/cvf5DUmxebylJpw.png)



①定义一个新的该数据类型变量只需要用类名，类似于用过typedef的结构体

#### **类与对象在内存中的存在形式**

![image-20230405164832338](https://s2.loli.net/2023/10/15/6eXxYDqBTVoHr2h.png)

③**属性（也称为 成员变量/field字段）**，其前面可添加访问修饰符

④**类的变量之间的赋值和数组一样，为地址传值**（因为都为引用类型）

#### *对象创建的内存流程

*（**对象本质在堆里边，p只是对象的引用**）

![image-20230405164846371](https://s2.loli.net/2023/10/15/rQp8b2UFnASORNY.png)





------

### 方法（函数）

①在方法定义的数据类型前面的为访问修饰符

（**public / protected / 默认 / private**），**不写为<u>默认</u>**，

##### 方法重载：

**Java允许在同一个类中，多个同名方法的存在，但<u>调用的形参类型</u>不能完全一致。使用时根据填入形参不同调用不同的方法。**

①可变参数：java允许将同一个类中多个同名（0—N个），参数个数不同的方法，封装成一个方法	

注意：括号内只能出现可变参数且必须在最后（string不可变）

![image-20230405165011577](https://s2.loli.net/2023/10/15/jXpwm9zfLNY8UVR.png)

##### 方法重写/覆盖

**子类的一个方法和父类的方法返回类型，方法名称，形参列表全都一样。**

*①子类的方法返回类型一般要一样，也可以是父类返回类型的子类

*②**不能比父类方法的访问权限还要小**。比如父类是public，而子类是protected









#### ***方法的内存调用机制**

<img src="https://s2.loli.net/2023/10/15/VWpOaPSEQg6RUdh.png" alt="image-20230303194712421" style="zoom:67%;" />

①在调用方法（调用函数）时，**首先需要定义一个类封装**，然后再在类里边进行方法的定义。**使用时**，**需要先new一个类的对象**，(将类实例化)，然后在用  **对象.方法()**   ,进行方法的调用



②如果方法1和方法2在同一个类的话，在方法2里边可以直接调用方法1；

跨类的话，就需要先new个对象**（要符合权限）**，再去调用。



③方法里调用方法，就是不断开栈 **(方法栈)** ，然后再一个一个返回返回值，所以**在调用方法时，你传进去的<u>非引用参数</u>只在开的方法栈里边胡作非为，并不会影响main栈里边的变量。**即：

1.**基本数据类型，传递是值拷贝，形参的改变不会改变实参！！**

2.**引用类型（数组和类）反之，因为是地址传递，就会改变实参，**因为虽然调用的空间开在栈，但是**引入的地址所对应的空间才是操作的主对象**，主方法引用该数组时也是会去堆里边寻找详细的值。



易错！！

①![image-20230303203821575](https://s2.loli.net/2023/10/15/eSxOHFVlhZzbwEd.png)

这里是说的开辟的新空间里边的p**<u>不指向任何东西</u>**了

②如果在方法右边新创建了一个对象，那么会在开辟一个空间，不会影响原来的引用类型实参





------

#### equals和==

①==可判断引用类型和基本类型，**基本类型看具体的值**，**引用类型看地址是否相等**，而且给引用类型赋值引用类型也是给的地址。

②equals只能判断引用类型，**默认判断地址是否相等**

③



------

#### .toString

![image-20230402115451853](https://s2.loli.net/2023/10/15/DX5ko9YEGAmtT8P.png)



**可以重写toString类型进行调整对象的sout输出**

<u>`sout（对象名）`</u> 就是调用**对象.toString**



------

#### finalize（垃圾回收器）

![image-20230402115633878](https://s2.loli.net/2023/10/15/xN8UvS4HEWTJ2Py.png)





------

### 作用域

> ①全局变量：即类的属性||作用域：**整个类**||可以不赋值，有默认值
>
> 局部变量：一般是在成员方法内定义||作用域：**当前方法**||必须赋值，无默认值。
>
> ②全局变量和局部变量可以**重名**，**调用时候的值遵循就近原则**。
>
> ③全局变量可以**加修饰符**，但是局部变量不可以（因为作用域早已被限制）。
>





------

### 构造方法（构造器）

*①**无返回值也不能写返回值**，且**方法名必须和类名保持一致** 	

②主要作用是**完成对新对象的初始化**

③创建对象时，系统会**自动调用**该方法进行对对象的初始化。

<img src="https://s2.loli.net/2023/10/15/nibe2PDvsYUgwrB.png" alt="image-20230305195223828" style="zoom:67%;" />

④如果未定义构造器，系统会**自动生成一个无参构造器**（默认构造器）

⑤alt+insert快捷键可快速打出

*⑥子类构造器中，不管写不写，都会**先调用父类构造器**



------

### this关键字

①![image-20230305202226636](https://s2.loli.net/2023/10/15/nvICfwPdmuaqVs2.png)

②**this本质**

> ③哪个对象调用，this就代表哪个对象
>
> ④构造器里用this调用另外一个构造器时，需要把这句话放在构造器中第一行。
>
> ⑤p1.方法()------在定义方法时里边的this，指代的就是p1
>
> ⑥this()  意思是在一个构造器中调用另外一个构造器，括号内无参或者别的参数列表
>



------

### 包

> ①package  包名；
>
> ②包的本质：**创建不同的文件夹保存类文件**
>
> ③com.xoliu，**点就是下一级文件**
>
> ④一个类中**最多引用一个package**，且引用语句必须在**第一行**； import在类和包之间，可以有多条引用
>



------

### **访问修饰符

①<img src="https://s2.loli.net/2023/10/15/ukNjniGHWI26L3y.png" alt="image-20230306203259857" style="zoom:67%;" />

②上图的规则不仅适用于属性，也适用于方法

③只有默认和public可以修饰类(class)



------

### 封装

①![image-20230306204150228](https://s2.loli.net/2023/10/15/GnIMoxA5iDECdSu.png)

②alt+insert可快速打出，然后完善代码，在set里边进行输入的数据进行判断，get就是去返回用户的数据

③加入了数据的校验，增加了业务逻辑。

④**封装和构造器：**

将set写在构造器中，可以快速赋值和验证数据，更加方便；

![image-20230306210325401](https://s2.loli.net/2023/10/15/PJk4rjfDCslSi8g.png)

⑤







------

### 继承

①因为有时两个类的属性和方法是相同的，所以需要继承，即代码复用性

从这些类中抽象出父类，在父类中定义这些相同的属性和方法（**非private属性方法）**，子类就不需要再定义了，只需要通过 **extends** 声明继承父类即可。即

`class 子类 extends 父类{}`



②子类也可以当别的类的父类，该类自动继承父类和子类的属性和方法（非private属性方法）

③**非私有**的属性和方法可以再子类中**直接**访问

④私有的属性和方法，可以通过父类提供一个公共的方法去间接访问

比如 get属性（）或者

![image-20230307214548132](https://s2.loli.net/2023/10/15/rCvXSy5jEmMeH16.png)

![image-20230307214503970](https://s2.loli.net/2023/10/15/6IVk1QtxfoX3hOY.png)

⑤![image-20230307214848696](https://s2.loli.net/2023/10/15/IB5cU1A4D6Zk3TJ.png)

⑥接⑤，任何子类构造器，默认自动添加一句话为super()，其作用为**调用父类的无参构造器**

⑦如果父类没有无参构造器，子类调用自己的无参构造器时会报错）此时必须**手动调用父类的有参构造器**，用**super（）**去指定到底用父类的哪个构造器，括号里边按顺序**填调用的父类构造器的参数列表**，且**super要放在第一行**（他是这么讲的，但我码出来如果父类没写无参构造器，子类写了也能用

⑧什么都不写，默认认为调用父类的无参构造器，即 **super()**

⑨java中  **Object**是**所有类的父类**；对类ctrl+H，可查看类的继承关系

⑩父类构造器的调用不限于直系父类，会不断上溯到Object类

⑪子类只能继承一个父类，即java的**单继承机制**

⑫

------

##### 继承的本质(内存分配)

​		加载子类时，①方法区内先从object类开始往下加载，②然后在堆中为子类分配一个很大的空间，在这个大的空间里，③分别新建空间存储这个子类和父类爷类的属性(string是地址，指向常量池)，各类的空间相互独立，所以即使属性重名也不冲突，④将这个大空间的地址返回给main栈中new的对象。

​		如果爷类父类和子类的属性重名，访问属性时，将会先从子类查找，如果有且<u>**可访问**</u>，返回信息，不断往上找直到object类。

///不能访问该属性（private），但分配的内存中有该属性，可以通过public方法返回。

​		查找的过程中，**一旦遇到同名属性<u>且无法访问</u>**，将不会再往上进行查找，直接报错，不管爷类有无该属性。

![image-20230311111410527](https://s2.loli.net/2023/10/15/lQwKqHRaZ7y2m6t.png)



------

##### super

> ①**super()只能出现在构造器中，且只能放在第一行；**
>
> ②this()  和 super() 在构造器中都只能放在第一行，所以这两个不能共存在一个构造器中；有了this就没有super了。
>
> //**this()  意思是在一个构造器中调用另外一个构造器**，括号内无参或者别的参数列表
>
> ③Object的无参构造器什么都没输出
>
> ④super无法访问父类的**<u>private</u>方法和属性**---->super.name      super.age   用法和this类似
>
> ⑤如果子类和父类属性名重名，要想访问父类的属性（可访问），必须用**super.属性**来访问。如果没有重名，用this 或者super都行。**this是从子类开始往上找，super父类开始往上找**
>
> ⑥
>



------

### 多态

> ​    **==多态的前提：两个类存在继承关系==**
>

##### 对象的多态

①一个实例化的对象的**编译类型和运行类型可以不一致。**

②new时，“=”左边是编译类型，“=”右边为运行类型。

③编译类型定义时就已经定了，不可改变。运行类型可以改变

`Animal animal = new Dog();`

**如果要改变运行类型：   `animal = new Cat();`**



##### 向上转型

本质：父类的引用指向子类的对象

①**可以调用父类的所有成员**(看访问权限)。

②**不能调用子类的特有成员**（方法和成员）。特有成员就是**只有子类有，父类没有**。因为能调用哪些成员只和编译类型有关。

当调用的是父类子类共有的方法，即方法重写，会调用子类的方法。

即最终运行效果，还是得先从运行类型里边找方法，找不到再往上找父类。



##### 向下转型

上面说**无法调用子类的特有成员**，那么如何调用子类的特有成员？

![image-20230314204029220](https://s2.loli.net/2023/10/15/wtJkiGcfbzWqQla.png)

把父类的引用转换为子类的引用

`Cat cat = (Cat) animal;`

此时编译类型已经变成Cat了，这样做的前提：**在这之前animal的运行类型就得是Cat,才能进行向下转型**

也就是说：你只能把一个指向Cat的转成Cat，而不能转为Dog。



##### 多态数组

①建立一个既有父类也有子类对象的数组，`father[] fathers = new father[];`

定义类型为父类，数组元素实际类型可以为子类。

![image-20230323204427062](https://s2.loli.net/2023/10/15/j8HkcqOBnXKENQP.png)

②但是数组编译类型是父类，调用某一个类的方法时需要转型，可以通过遍历判断是啥运行类型，然后在进行转型然后调用方法。

遍历用 instanceof 判断运行类型是不是某个子类

![image-20230323205641942](https://s2.loli.net/2023/10/15/KviOUI1VALy6YnF.png)

③`对象名.getClass()`  将会返回该对象的运行类型。

④



------

### 动态绑定机制

①当调用对象方法时，**方法会和运行类型绑定**，如果有个向上转型，调用方法时会**从运行类型开始往上找**，找到的方法中如果调用了别的方法，调用这个别的方法时**也是从运行类型开始往上找**，而且从哪个类调用，变量就用那个类里的变量（局部变量规则）。

②



------

### 类变量/静态变量

> ①在一个类中定义了一个类变量(static)，该类所实例化的**所有对象都能共享这个变量**
>
> 即    **`访问修饰符 static 数据类型 变量名`**    	**因为有访问修饰符，需遵循访问权限**
>
> ②**类变量是跟<u>类的加载</u>一起创建**的，所以**没有将类实例化也可以访问**或者加载，
>
> 类变量和类同生共死，类的消亡也随着类变量的销毁。
>
> ③类变量也可以通过类名/对象名来访问，例如`child.count`	or `child1.count`
>
> ④类变量的jdk8以后，默认认为类变量的内存在**这个类在堆中的空间后边。**
>
> ⑤类变量和实例变量的区别:实例变量没有static，且实例变量不能用**类名.变量名**访问
>

------

### 类方法

①方法用了**static**修饰之后，方法就是静态方法，定义方式大差不差

*②静态方法内**只可以访问静态变量**

③![image-20230402124356152](https://s2.loli.net/2023/10/16/PsW8mArRbBS7vM3.png)

*④类方法不能使用**this**、**super**等词汇，可调用的话不符合静态的理念。而且也**只能访问静态方法和静态变量**  but但是普通的成员方法所有访问权限内的变量均可访问（包括静态非静态）

⑤类方法里可以自定义新变量，并且再方法中访问和使用。 注（main方法就是个典型的例子）

*⑥**static方法不能重写**

⑦

------

### main方法

##### main方法语法

> ①jvm需要调用main（），所以必须是public，调用时**不进行实例化**，所以也需要加**static**
>
> 该方法接收**String类型的数组**，这个数组保存执行java命令时传递给运行类的参数。
>
> void是因为虚拟机不需要返回值
>
> ②main也是一个类，我们可以在main所在的类(即唯一的public类)中，定义静态变量，静态方法，main()中可以直接用，因为main是静态方法，所以你在这个类定义的非静态变量，在main()里是无法使用的。
>

##### main动态传值

![image-20230402131414756](https://s2.loli.net/2023/10/16/cDuPei97bB1RvjH.png)

![image-20230402131503562](https://s2.loli.net/2023/10/16/KGyaQ3TrRsitPxY.png)



------

### 代码块（初始化块）

##### 代码块基本语法

```java
【修饰符】{ 

	代码

};
```

①修饰符可有可无，写的话**只能写static**

② ';' 可以写也可以忽略

##### 使用细节

> ①类中各个方法相同的语句，就可以放入一个代码块中，代码块中的内容，**调用任意一个构造器时（创建对象）**时，<u>都会**首先运行代码块**中的语句，***代码块优先于构造器**</u>
>
> ②代码块分为静态和非静态，静态代码块我们都知道静态的东西**随着类的加载而执行**，所以**静态代码块只会执行一次**。但是**普通的每new一次就执行一次**，因为↓
>
> *③静态代码块内的内容，**只要<u>加载了类</u>就执行**，甚至在我们输出某一个类的一个静态变量时，因为访问静态变量就会加载类，加载类就会运行静态代码区中的内容，普通的则不会运行，但是只使用静态成员时，普通的代码块不会运行。因为静态和普通的他们的内存并不在一起，**两个作用域是分开**的。
>
> ④普通代码块是构造器的一种补充，就像是夹在**每一个构造器的第二个语句**。**第一个是	`super()`**   
>
> *⑤静态代码块**优先于**构造器中super()和普通代码块，因为它在**加载类时就已经执行完毕**
>
> ⑥静态代码块和静态方法一样，**只能调用静态成员**，**普通代码块可以使用任意成员**。
>



------

### * <u>[重要!]类什么时候被加载</u>

①new一个对象时

②new一个子类对象时，**父类的也会被加载**。（先加载父类的代码块）

③**访问某个类的静态方法或者静态变量**时。

tips：每加载一次，静态代码块就会执行。

------

### <u>*new对象时，类中的调用顺序</u>

*原则： **先进行类的加载，在创建对象**

##### 普通类

> ①**先运行静态**变量初始化内容和静态方法，多个静态成员的话，按先后顺序运行。
>
> ②**再运行普通**变量的初始化和普通方法，多个普通成员按先后顺序
>
> ③最后运行构造器和其他构造方法
>

##### 继承的类

> ①父类的静态代码块和静态成员
>
> ②子类的静态代码块和静态成员                             
>
> ③父类的普通代码块和普通成员初始化
>
> ④父类的构造方法
>
> ⑤子类的普通代码块和普通成员初始化
>
> ⑥子类的构造器方法
>

***keys：先运行父子类的静态，这部分优先于类先运行，在加载父类，然后加载子类。**

**tips：对以上同一级别的成员，按定义先后顺序运行。**



------

### final

**const？**

#### *使用到final的情形

> ①**不希望被继承**。加了final就不能被继承了，也就不会有子类，
>
> ②**不希望被子类重写**，加了后，子类就无法重写加了final的父类方法。
>
> ③**不希望类的某个属性被修改**
>
> ④**不希望某个局部变量被修改**
>

#### final细节

> *①定义final修饰的变量**必须有值**，**构造器中或代码块中赋值也可以**
>
> ②如果final变量是静态的，那么它的区域在静态域，**构造器无法给他赋值**，所以就不能在构造器中赋值，只能 **1.定义时赋值 2.静态代码区中赋值**
>
> ③如果类不是final类，但其中有一个final方法，那么这个方法尽管**不能重写，但是可以被子类继承。**
>
> ④如果一个类已经是final类，没有必要在里边定义final方法，因为都**不能继承**了，也就**无法实现方法重写**。
>
> ⑤**final不能修饰构造器**
>
> ⑥final和static一起用效率很高，调用时，就**不会加载类**，也就**不会运行静态代码块**的内容。
>

------

### 抽象类（abstract）

#### 抽象方法引入

> ①**当父类的某些方法，不确定如何实现，就可声明为抽象方法（用abstract修饰），那么这个类就是抽象类。**
>
> ②所谓抽象方法就是**没有实现**的方法，没有实现的方法就是**没有方法体**。
>
> ③抽象类会被子类继承，在子类中不同方式实现。
>

#### 抽象方法细节

> *①<u>一个类中存在抽象方法，那么这个类就**必须声明为抽象类**</u>。但一个**抽象类中可以没有抽象方法**
>
> *②**抽象类不能被实例化**（new)
>
> ③abstract**只能修饰类和方法**
>
> ④**抽象类的本质还是类**，所以也可以有静态成员构造器等。
>
> *⑤**抽象类的子类必须实现所有抽象方法**，**除非他自己也声明为抽象类**
>
> *⑥抽象类和方法**不能被private、final，static修饰**，因为抽象方法<u>必须被重写</u>，但是这三个词都和重写相违背。





------

### 接口（interface）——”完全抽象“的类

#### 接口引入

接口给出一些**<u>未实现</u>的抽象方法<u>封装</u>**在一起，需要用时，**根据具体情况补充方法体**

接口中，方法**都是抽象方法**，写不写abstract都行

#### 使用细节

> ①类接入接口时，需要在声明类时**implements 接口名字**（可以接多个接口）
>
> *②接口中可以写入**带有<u>default</u>的方法体**和**静态方法**
>
> *③**接口不能被实例化**，且**接口中的所有方法必须为public**
>
> *④一个**普通类**接入接口需要**实现该接口的所有方法**
>
> ⑤对应④，**抽象类**接入接口时，**不用实现所有方法**，因为它巨J8抽象
>
> *⑥接口中的**<u>所有属性都是 public  static  final</u>**  理由：根据接口的理念，你完全可以在接入接口的类中<u>（接口名.属性名）</u>访问接口的属性，且**无法修改该属性（final）**
>
> ⑦**接口<u>不能继承类</u>，但可以继承别的接口**
>



#### 接口与继承

继承的价值：代码的复用性和可维护性

接口的价值：设计一个规范，让其他类去实现，更加灵活

###### 	**接口就是抽象义父！！！！**

#### *接口与多态

**接口就是义父**，那么义父能不能像父类那样**向上转型**吗？答案是可以。

<img src="https://s2.loli.net/2023/10/16/qSwoIp9aGcReZ51.png" alt="image-20230403211839518" style="zoom:50%;" />

这里**并不是接口实例化**，而是**接口指向了实现了该接口的对象实例**

这不就是多态里边的**向上转型**吗？那能实现多态数组吗？当然也可以

<img src="https://s2.loli.net/2023/10/16/aYfnjIwbBvT5pDO.png" alt="image-20230403213439516" style="zoom:50%;" />

诶？**接口不是不能实例化**吗？这怎么回事？

*****实例化是什么，就是**创建对象**，而我们**<u>开数组是在内存先开辟空间，而给数组空间赋于对象才是实例化</u>**

实例：<img src="https://s2.loli.net/2023/10/16/rbBKd5Avt1iVZaf.png" alt="image-20230403213920512" style="zoom:50%;" />

##### 接口的多态传递

如果一个类接入了子类接口，那么这个类可以进行**子类接口的向上转型**，理所应当，也可以进行**父类接口的向上转型**，实现父类接口的方法。





------

### 内部类

#### 类的五大成员

**<u>属性、方法、构造器、代码块、内部类</u>（可以直接访问私有变量）**

#### 内部类的分类

##### 定义在外部类局部位置上（方法或代码区内）

1）**局部内部类** (有类名)      *2）**匿名内部类**(无类名)

##### 定义在外部类的成员位置上

1）**成员内部类** (无static)   2）**静态内部类**(static)

tips：外部类中和内部类中**变量重名**，在**内部类中访问该变量返回的是内部类的初始化值**，想访问外部类的值**->**`外部类名.this.变量名`

#### 局部内部类

①**不能有访问修饰符**（地位是局部变量），***但可以用final***（局部变量可以用final）

*②作用域**仅局限于所处的方法内或代码区**内，超过作用域的地方无法访问

③可以在**作用域内**new这个局部类并**调用**这个类的方法；

*④<img src="https://s2.loli.net/2023/10/16/uaOCUMKvoL2EVcQ.png" alt="image-20230404082651430" style="zoom:67%;" />



#### *匿名内部类

#### 引入

特点：1）没有给名字  *2）**还是一个对象**

语法：`new类 或接口（参数列表）{（类体）}`

如果某个类只使用一次，就可以用匿名内部类简化开发。

*匿名内部类可以让我们在某个类中的**方法或者代码区**中，**"个性化"的重写调用的类**并且**不会影响调用类原类**，因为作用域仅仅局限**这个方法或者代码区**中。

<img src="https://s2.loli.net/2023/10/16/gjNX2ETorxBHL6U.png" alt="image-20230404085043838" style="zoom:50%;" />

*这个对象(tiger)的**编译类型是接口**，运行类型就是这个**匿名内部类（系统底层分配命名然后去继承原类）**。

所以这个对象等同于**匿名内部类的实例化**，而不是接口的实例化（接口不能实例化）

基于类的匿名内部类写法很容易发现就是普通的new对象多了一个**<u>”{}“</u>**

个人认为，匿名内部类，是对**接口或者原类的方法的‘个性化’方法重写**；到时候的运行类型，就是系统**隐性**自动**生成了一个类**，这个**类继承了编译类型**，方法体内的是对父类方法的重写。（如果原类是抽象类，就必须对所有方法重写，不然会报错）以下印证以上

<img src="https://s2.loli.net/2023/10/16/WLs6Q84AN1S3OiZ.png" alt="image-20230404123609936" style="zoom:50%;" />



#### 成员内部类

视为**类的一个成员**就行，作用域只在**这个类**以内；

##### 其他类用成员内部类：

①需要在**外部类中写一个方法调用这个内部类中的方法**，然后在别的类调用这个类的这个方法

*② `外部类对象.new   内部类()`			相当于先new一个外部类对象，然后在**调用对象.new 内部类**，（推荐）

③外部类写个方法，返回 `new   内部类对象`    用的时候先new外部类对象，然后调用外部类对象.var，相当于new，然后用。

![image-20230405183946475](https://s2.loli.net/2023/10/16/bqxl5NKoz1VSgDt.png)



#### 静态内部类

<u>比成员内部类多了一个static</u>

##### 外部其他类访问静态内部类

①同上的“*②”

同上，定义的方法可以是static，这样的话**不用创建外部类对象**就可以调用方法。

tip：访问静态内部类的静态成员直接用`外部类.内部类.变量`就可以





------

------

------

## 应用性知识

### 枚举类

#### 使用

##### 自定义枚举类的实现

> ①**构造器私有化**，new只能在本类执行，并**去掉所有set()方法**，防止值被修改。
>
> ②创建固定的**final static枚举常量**；
>
> ③访问时直接 `类名.枚举常量`
>

<img src="https://s2.loli.net/2023/10/16/YJ8Wr4MmkzXwifT.png" alt="image-20230405191224516" style="zoom:80%;" />

##### 关键字枚举类的实现

> ①**类名前的class改成enum**
>
> ②**构造器私有化**
>
> ③多个枚举常量需要**逗号分隔，分号结束**。
>
> ④**枚举常量放在最前边**
>

#### 细节

> ①枚举常量命名通常全部**大写**
>
> ②当我们用enum实现枚举类时，其实是继承Enum类，并且已经是final了
>
> ③如果使用无参构造器，定义枚举常量也可以直接简化成不写括号的形式。
>
>  ④枚举类**可以实现接口**，但是**不能再继承别的类**了

<img src="https://s2.loli.net/2023/10/16/2nOSCo6LzuQltkq.png" alt="image-20230405193050725" style="zoom:80%;" />

#### Enum成员方法

> ①**toString**--->`return name`   输出枚举常量**名称**
>
> ②**枚举.ordinal**       返回该枚举类型的**编号（从0开始）**<img src="https://s2.loli.net/2023/10/16/JkmRFDnHE9GxVWl.png" alt="image-20230405194122530" style="zoom:80%;" />
>
> ③**values**    **返回一个含有所有定义的枚举常量的数组**
>
> <img src="https://s2.loli.net/2023/10/16/o7Oi1VarTHj4SyX.png" alt="image-20230405195256444" style="zoom:80%;" />
>
> ④**valueOf（）**    将括号内的**字符串**转为枚举变量
>
> ⑤**compareTo** 	比较两个枚举常量，**比较的是编号**
>



------

### 注解（Annotation）

#### 三个常见注解

**@Target是修饰注解的注解**，称为”<u>元注解</u>“

##### @Override

> ①表示下边的方法重写了父类方法，**没写也不能表示不是重写**。
>
> ②有这个注解后，系统**就会<u>检查</u>是否真正重写了父类方法**，**没有重写就会报错**
>
> ③**Override只能修饰方法**
>

##### @Deprecated

> ①表示某个元素过时，即**不再推荐使用**，但仍然可以使用。
>
> ②一般用来做版本升级和过渡使用
>

##### @SuppressWarings{“   ”}

> ①不想看到警告，用来抑制警告信息
>
> ②**大括号内填写屏蔽什么类型的警告**，例如**("all")**
>



------

### 异常（Exception）

#### 引入

**<u>我觉着是：忽悠编译器</u>**

快捷键 ： ***ctrl+alt+t***

<img src="https://s2.loli.net/2023/10/16/VbQRTjovyG9ZIn5.png" alt="image-20230406140603915" style="zoom:67%;" />

<img src="https://s2.loli.net/2023/10/16/aORm4XZez9v6QqL.png" alt="image-20230406141057062" style="zoom: 50%;" />

<img src="https://s2.loli.net/2023/10/16/MIBLy35RfibvqdF.png" alt="image-20230406141149069" style="zoom:67%;" />

![image-20230406141711817](https://s2.loli.net/2023/10/16/UOnLGfE8xc14wkq.png)

#### 常见运行时异常

> ##### ①空指针异常
>
> <img src="https://s2.loli.net/2023/10/16/6Y38UEtTBIaWl1G.png" alt="image-20230406183843191" style="zoom:67%;" />
>
> ##### ②数学运算异常
>
> 一个数除以0
>
> ##### *③数组下标越界异常
>
> 下标越界
>
> ##### ④类型转换异常
>
> ##### ⑤数字格式不正确异常
>

#### 异常处理机制

##### try-catch-finally

>  <img src="https://s2.loli.net/2023/10/16/34VZnsk9cJAFrIj.png" alt="image-20230406184932670" style="zoom:50%;" />
>
> ①如果异常发生了，则**异常不会执行**，**直接执行catch块。**
>
> *②也可以进行**try-finally （没有catch捕获异常）**，所以会导致**不管发生不发生异常，都会执行finally内容**

##### throws(甩锅机制)（系统默认调用的）

> <img src="https://s2.loli.net/2023/10/16/3zOpomHcSVvxhsF.png" alt="image-20230406185725786" style="zoom:50%;" />
>
> <img src="https://s2.loli.net/2023/10/16/KpaRH2N1fmsdVCB.png" alt="image-20230406210241676" style="zoom:67%;" />
>
> 别的方法**调用一个编译异常方法**时，即使原方法抛出编译异常了，**仍然会报错**。这时，**我们可以在这个方法抛出和原方法一样的异常**，或者**在这个方法内对这个调用进行t-c-f**；**运行异常则不会**
>

###### throw和throw的区别

<img src="https://s2.loli.net/2023/10/16/OyMw9osxGVauQNA.png" alt="image-20230407100713377" style="zoom:50%;" />



#### 实践

##### 如果用户输入的不是一个整数，就提示，直到输入的是整数

<img src="https://s2.loli.net/2023/10/16/5etN8phSKox7m9c.png" alt="image-20230406201427234" style="zoom: 50%;" />

------

### java绘图

```java
public class drwa extends JFrame {  //JFrame对应窗口，可以理解为一个画框
    private Panel mp = null;
    public static void main(String[] args) {
        drwa drwa = new drwa();//创建对象并完成初始化，将会弹出画的画
    }
    public drwa(){  //
        //初始化面板
        mp = new Mapanel();
        //把画放进画框里
        this.add(mp);
        //设置窗口大小
        this.setSize(400,300);
        //让窗口可视化
        this.setVisible(true);
    }
}
class Mapanel extends Panel{    //自定义类继承Panel类
    @Override
    public void paint(Graphics g) { //g可想成画笔
        super.paint(g); //调用父类的方法进行初始化
        //Panel中有很多api可调用，例如
        g.drawOval(50,50,200,200);
    }
}
```





------

------

------

## *集合框架

<img src="https://s2.loli.net/2023/10/16/uVvscrRHodNZMGE.png" alt="img"  />

------

------

------

## Collections接口

### *Collections接口常用方法

> `add()`	**括号内添加的单个元素**	可以是对象实例化，比如`add(new 构造器）`	
>
> `remove()`	**括号内填删除第几个元素或某个详细的元素**
>
> `contains()`	**查找某个元素是否存在**
>
> `size()`	**返回 元素个数**
>
> `isEmpty()`	**判断是否为空**
>
> `clear()`	**清空这个集合**
>
> `addAll()`	**添加多个元素，括号内是接入Collections接口的集合。**
>
> `removeAll()`	**同上，删除多个元素**
>
> `Collections.reverse();`  **次序翻转，无返回值，在原集合上修改**



#### *集合增强for

**<u>简化版的Iterator迭代器遍历</u>**

<img src="https://s2.loli.net/2023/10/16/ufVpkxMt5aoACSn.png" alt="image-20230410201628979" style="zoom:67%;" />

------

## List接口（有序可重复）

![image-20230410202438135](https://s2.loli.net/2023/10/16/sTMLdxNhtQjSIcm.png)

##### 除父接口特有方法

> `add(index,obj)`	**将obj插入到index位置后边**
>
> `addAll(index,集合)`	**将集合插入到index位置后边**
>
> `indexOf(obj)` 和 `lastIndexOf(obj)`	**返回obj在集合整首次和末次出现的位置**
>
> `remove(index)`	**移除index索引的元素，并返回该元素** 	
>
> *`set(index,obj)`	**设置index位置的元素为obj**
>
> `subList(a,b)`	**返回从a到b-1索引的子集合**



------

#### ArrayList

①可以`add(null)`

②**线程不安全，效率高**

**底层结构和源码分析**:

①ArrayList底层维护的是一个object的**<u>数组</u>**elementData（transient 瞬间，表示不会被序列化）

②用**无参构造器**创建对象时，**初始的容量为0，第一次添加会扩容为10，如果需要再次扩容，会扩容到1.5倍**

③如果用的有参int构造器，则初始的容量为指定大小，需要扩容则**直接扩容1.5倍**

④扩容用的**Array.copyOf()**



------

#### Vector

①<u>protect</u>的object数组，**线程安全，效率不高**

②扩容机制和ArrayList类似，**初始容量为10，扩容倍数为2倍**

#### *Vector子类Stack常用方法

```java
Stack stack = new Stack();
```

> `push(E item)` 返回值 E
>
> `pop()` 返回值 E
>
> `peek()` 返回值 E	将栈顶元素返回，但是不从栈中移除它
>
> `empty()` 返回值 boolean	判断栈是否为空
>
> `search(Object obj);` 返回值 int - 基数为1，返回对象在堆栈中的位置，以 1 为基数。如果对象 obj 是堆栈中的一个项，此方法返回距堆栈顶部最近的出现位置到堆栈顶部的距离；堆栈中最顶部项的距离为 1。



------

#### LinkList

①底层**<u>双向链表</u>**和**<u>双端队列</u>**

②可以**添加重复元素包括null**

③线程不安全



------

## Queue接口

> 压入元素(添加)：add()、offer()
> 相同：未超出容量，从队尾压入元素，返回压入的那个元素。
> 区别：在超出容量时，add()方法会对抛出异常，offer()返回false
>
> 弹出元素(删除)：remove()、poll()
> 相同：容量大于0的时候，删除并返回队头被删除的那个元素。
> 区别：在容量为0的时候，remove()会抛出异常，poll()返回false
>
> 获取队头元素(不删除)：element()、peek()
> 相同：容量大于0的时候，都返回队头元素。但是不删除。
> 区别：容量为0的时候，element()会抛出异常，peek()返回null。



------

#### Deque 

> deque“double ended queue（双端队列）”的缩写，双端队列顾名思义就是**队列的两个端口都能进出**。

①有三种用途

```java
 - 作为普通队列（先进先出）
 Queue queue = new LinkedList()或Deque deque = new LinkedList()
 - 作为堆栈（先进后出）
 Deque deque = new LinkedList()
- 作为双端队列（两端可进出）
Deque deque = new LinkedList()
```

##### 常用方法

> ![image-20230417200434581](https://s2.loli.net/2023/10/16/8pv3hQFDEOgRCzm.png)

**<u>Java官方推荐使用Deque替代Stack使用</u>**





------

## Set接口（底层Map）

![image-20230411181358408](https://s2.loli.net/2023/10/16/YOlKNDUcdfHoJAS.png)

*①**不能用索引方式来获取元素**

*②无序（即**添加顺序和取出顺序不一致，但取出顺序固定**）

------

#### HashSet（底层HashMap）

①可以放null，但只能有一个null；

*②add操作会返回一个**<u>布尔类型</u>表示是否添加成功**。也就是表示原set是否含该元素(哈希值再处理，进行判断)

*③底层扩容机制

![image-20230412132633589](https://s2.loli.net/2023/10/16/kb4MFl8dyf9NqDu.png)

④

------

#### LinkedHashSet（数组+双向链表）

①根据**哈希值**决定元素位置。

![image-20230412135155774](https://s2.loli.net/2023/10/16/tqPeZXral5Eo9IF.png)

②取出顺序和添加顺序一致

------

#### TreeSet

①**输出时默认按字典序或者数字大小排序而输出**

或者按照自定义的排列规则

![image-20230416153912904](https://s2.loli.net/2023/10/16/ETU3isF7uH92ReI.png)



------

------

## Map接口

![image-20230412185252466](https://s2.loli.net/2023/10/16/9phrAlSDNJGs14U.png)



### **Entry**

由于Map中存放的元素均为键值对，故每一个键值对必然存在一个映射关系。
Map中采用Entry内部类来表示一个映射项，映射项包含Key和Value (我们总说键值对键值对, 每一个键值对也就是一个Entry)
Map.Entry里面包含`getKey()`和`getValue()`方法

### ①HashMap

①put相同的key时，会对**原来的key所对应的value**进行<u>覆盖</u>。

②**key、value都可以为null**；但只能有一个key为null（**<u>因为key不能重复</u>**）

> **`.get(key)`** 
>
> 可以得到**key所对应的value**
>
> `int size();`
> **获取集合中元素的个数。**
>
> `void clear();`
> **清空集合，元素个数变为0。**
>
> `void remove(key);`
>
> **删除key所对应的键值对**
>
> `boolean isEmpty();`
> **判断集合元素个数是否为0。**
>
> `boolean containsKey(Object key);`
> **判断集合中是否包含指定key。**
>
> `boolean containsValue(Object value);`
> **判断集合中是否包含指定value。**
>
> `keySet()`	
>
> **该方法返回map中所有key值的列表，用set接收**
>
> `.getOrDefault(Object key, V defaultValue)`	
>
> **有这个key时，就返回这个value值，如果没有就返回defaultValue。**

#### **遍历操作：**

##### key

<img src="https://s2.loli.net/2023/10/16/i9MUYCkBuglPWRa.png" alt="image-20230412193658194" style="zoom:67%;" />

##### value

<img src="https://s2.loli.net/2023/10/16/BazmAgcHRPNpQlj.png" alt="image-20230413192741997" style="zoom:67%;" />

##### k-v

<img src="https://s2.loli.net/2023/10/16/bai4phUAT2EcSHY.png" alt="image-20230413193159158" style="zoom:67%;" />

------

### ②Hashtable

①**k-v均不能为null**

②HashMap和Hashtable

![image-20230413200445967](https://s2.loli.net/2023/10/16/xvDRzbtVZyHJef4.png)



------

### ③Properties（io）

①Properties的k - v均为**字符串类型**，且均不能为null

②该集合可以从 **xxx.properties文件**中加载数据到该集合对象中。   

③

------

### ④TreeMap

![image-20230416154922388](https://s2.loli.net/2023/10/16/YFjfrRNgZWPnQkx.png)

put时**有重复的时候**，**不对原来的进行替换value**，而是**不进行操作**。































------

------

------

## *集合的选择

![image-20230416154433633](https://s2.loli.net/2023/10/16/yU3DsOKG2LpgaeW.png)



------

## IO流

### 文件流

![image-20230419121809271](https://s2.loli.net/2023/10/16/Mt7WyUHQfhEb9oe.png)

#### 常见的文件操作

##### ①创建文件

> ![image-20230419122006874](https://s2.loli.net/2023/10/16/fIZCUP2LugsleiG.png)

这里只是在内存中new了，如果想同步到磁盘中，需要调用`file.createNewFile()`	

```java
File file = new File("D:\\xoliu,123");
try {
    file.createNewFile();
    System.out.println("文件创建成功");
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

##### 获取文件信息

> `file.getName()`	**获取文件名字**
>
> `file.getAbosolutePath()`	**获取<u>绝对</u>路径**
>
> `file.getParent()`	**获取父级目录**
>
> `file.length()`	**文件大小（<u>字节</u>）**UTF-8下，英文1字节，中文3字节
>
> `file.exists()`	返回**文件是否存在**的布尔变量
>
> `file.isFile()`	返回**文件是否是一个文件**的布尔变量
>
> `file.isDirectory()`	返回**文件是否是一个目录**的布尔变量

##### 目录操作和文件删除

> `file.delete()`	删除文件，返回**删除结果的布尔变量**
>
> `file.mkdir()`	创建**单级**目录，返回结果的布尔变量
>
> `file.mkdirs()`	创建**多级**目录，返回结果的布尔变量

### 流的原理和分类

![image-20230419130540187](https://s2.loli.net/2023/10/16/Tz7hJiW5pI1uxtB.png)

------

#### 字节输入流(InputStream)

##### 构造方法

```java
new FileInputStream(File)		//File变量
new FileInputStream(String)		//绝对路径
new FileInputStream()			//
```

##### 常用操作方法

> `read()`	<u>**返回-1，表示读取完毕。**</u> 

 从输入流读取**<u>一个字节</u>**的数据，直至没有输入可用（中文三个字节）

返回类型为**<u>int</u>**，**记得类型转换**。



> `read(byte[] b)`	 返回值是**实际读取的字节数**，**返回-1时，读取完毕**

**最多读取 `b.length` 个长度的字节**



> `.close()`	//关闭文件流

 建立输入流，最后要记得进行**关闭文件流，释放资源**

- tips:建议加在**t-c-f的finally**里边


------

#### 字节输出流(OutputStream)

```java
FileOutputStream fileOutputStream = new FileOutputStream(file);
//覆盖写入
FileOutputStream fileOutputStream = new FileOutputStream(file,true);
//追加写入
```

- 如果**没有文件，会创建文件**，前提是**目录存在**

  

> ![image-20230419194709911](https://s2.loli.net/2023/10/16/lw41hvxYCAV7kur.png)

可写入一个**字符**或者**字节数组**

或者字符串

```java
fileOutputStream.write("Hello,World!".getBytes());
```

*tips：字符串里边输入“\n”，真的会回车换行！

##### *拷贝操作

```java
String path = new String("D:\\xoliu.txt");
String aimpath = new String("A:\\xoliu.txt");
File file = new File(path);
byte[] bytes = new byte[1024];
int readlen = 0;
try {
    FileInputStream input = new FileInputStream(file);
    FileOutputStream output = new FileOutputStream(aimpath);
    while ((readlen = input.read(bytes)) != -1){
        output.write(bytes,0,readlen);//这里需要注意，防止出错
    }	//边读边写
} catch (IOException e) {
    throw new RuntimeException(e);
} finally {
    System.out.println("拷贝完成！");
}
```

*这里注意，在写入文件时，按照

```java
output.write(bytes,0,readlen);
```

这样能保证**最后一组数据完美录入**



------

#### 文件字符流（FileReader）

##### 构造方法

> ```java
> FileReader reader = new FileReader(File);
> FileReader reader = new FileReader(String);
> ```

- **读取数据和字节输入流的read使用方法一样**

> `.read()`或者 `.read(char[])`



------

#### 文件字符流（FileWriter）

##### 构造方法

```java
FileWriter writer = new FileWriter(File);
FileWriter writer = new FileWriter(String);
//后边加true，则表示追加模式，否则为覆盖模式
```



##### 写入方法

```java
write(int)						//写入单个字符（Ascii）
write(char[])					//写入指定数组
write(String)					//写入字符串
write(String/char[],off,len)	//写入指定部分，len为偏移量	
```

- tips：使用完FileWriter后，必须要**<u>关闭(close)或刷新(flush)</u>**，否则无法写入指定文件



------

#### *节点流和处理流

 ![image-20230420173208401](https://s2.loli.net/2023/10/16/ysWFzZrg4p7Jvwi.png)



------

#### 对象处理流

> 不仅保存数据的值，也**保存数据的数据类型**，读取时也能直接恢复回这个数据类型，即：**序列化和反序列化**

![image-20230420180000711](https://s2.loli.net/2023/10/16/AmPlyunNYxVd7rF.png)

- 序列化后，保存的文件格式，不是txt，而是按照它的格式保存。

  ```java
  try {
      ObjectOutputStream  obj  = new ObjectOutputStream(new FileOutputStream(path,true)); 
      //上边注意构造器中new File...，并且根据需求加true
      obj.write(645);
      obj.write('s');
      obj.writeBoolean(true);
      obj.writeObject(new car("宝马"));
      //new的对象所属于的类，也需要支持序列化，也就是自定义接入Serializable接口。
      obj.close();
      //不可忘记关闭
  } catch (IOException e) {
      throw new RuntimeException(e);
  }
  
  class car implements Serializable{}//使其可序列化
  ```

- 反序列化需要和**保存数据的顺序**一致

```java
try {
    ObjectInputStream  obj  = new ObjectInputStream(new FileInputStream(path));
    try {
        System.out.println(obj.readObject());
       	//返回型是Object
        //会抛出异常需要处理
    } catch (ClassNotFoundException e) {
        throw new RuntimeException(e);
    } finally {
    }
    System.out.println(obj.readBoolean());
    System.out.println(obj.readChar());
    System.out.println(obj.readInt());
    obj.close();
} catch (IOException e) {
    throw new RuntimeException(e);
} 
```



如果我们需要调用文件中的对象， 需要**向下转型**，即：

```java
Object car = obj.readObject();
car car1 = (car) car;
System.out.println((car1.a);
```

![image-20230420192831335](https://s2.loli.net/2023/10/16/N4bVh6SlgpqjfL9.png)



------

#### 标准输入输出流

|          | System.in           | System.out  |
| -------- | ------------------- | ----------- |
| 编译类型 | InputStream         | PrintStream |
| 运行类型 | BufferedInputStream | PrintStream |

![image-20230424213603918](https://s2.loli.net/2023/10/16/Zmp3OkRiuByDKh2.png)



![image-20230424214252074](https://s2.loli.net/2023/10/16/DB1pNi4PotXmLKr.png)



------

## 线程基础

------

------

- 单线程：同一个时刻，只允许执行一个线程
- 多线程，同一个时刻，可以执行多个线程
- 并发：多个任务交替执行（单核cpu的多任务就是并发）
- 并行：同一个时刻，多个任务同时进行（多核cpu可以实现并行）

#### 线程的创建

##### 继承Thread类

> 1. 当一个类继承Thread类，该类可以当作一个线程
> 2. 我们可以重写run方法，写上自己业务代码
> 3. 再new 该类，即可创造线程，调用`.start()`，即可启动线程
> 4. `start()`  会启动线程，最终还是调用`run()` ,只单独调用run，没有真正创建了一个线程，会堵塞在主线程中。

##### 接入Runnable接口

> 1. 让一个类接入Runnable接口，并重写run方法
>
> 2. 创造线程时，不仅需要new对象，还要
>
>    ```java
>    Thread thread  = new Thread（对象）;	//对象为new的线程类实例
>    thread.start();
>    ```
>
>    

- 终端输入	`jconsole`	打开**<u>java监视和管理控制台</u>**

------

#### 线程常用方法

> ![image-20230425200647064](https://s2.loli.net/2023/10/16/8Sc6YbmAjXC3loO.png)
>
> ![image-20230425201201518](https://s2.loli.net/2023/10/16/Yc8eX56Nr2fPItK.png)
>
> `.getState()`	**获取状态**



------

#### 守护线程

> 当我们希望**main线程结束后，子线程自动结束**，将子线程设为<u>守护线程</u>即可
>
> 在启动 `start()` 前调用：
>
> ```java
> thread.setDaemon(true);
> thread.start();
> ```



------

#### 线程七大状态

- [`NEW`](#NEW)
  尚未启动的线程处于此状态。 
- [`RUNNABLE`](#RUNNABLE)
  在 Java  虚拟机中执行的线程处于这种状态。 
- [`BLOCKED`](#BLOCKED)
  阻塞等待监视器锁的线程处于此状态。 
- [`WAITING`](#WAITING)
  无限期等待另一个线程执行特定操作的线程处于此状态。 
- [`TIMED_WAITING`](#TIMED_WAITING)
  等待另一个线程执行操作达指定等待时间的线程处于此状态。 
- [`TERMINATED`](#TERMINATED)
  已退出的线程处于此状态。 

**新建	等待	就绪	运行	休眠	阻塞	死亡**



------

#### 线程同步机制

- 一些敏感数据不允许被**多个线程同时访问** ，就可以使用**同步访问技术**

> ​	线程同步，即当有一个线程在对内存进行操作时，其他线程**都不可以**对这个内存地址进行操作，**直到该线程完成操作**，其他线程才能对该地址进行操作。
>

##### 如何实现同步

```java
//1.同步代码块
Synchronized （对象）{	//得到对象的锁，才能操作同步代码
	//需要被同步的代码
}

//2.同步方法
public synchronized void f1(){	//同一个时刻，只能有一个线程执行f1()
	//方法体
}
```

示例：

```java
int i = 0;
public synchronized void sell() throws InterruptedException {
        System.out.println( Thread.currentThread().getName() + "已售出" + i + "张票");
        ++i;
        Thread.sleep(1);
}
@Override
public void run() {
    super.run();
    while(i < 100){
        try {
            sell();
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
    }
    }
```

- 方法体内利用代码块进行同步：

```java
synchronized (this){ 
    //代码内容    
}
```



> synchronized方法控制对 “对象” 的访问，每个对象对应一把锁，**每个synchronized方法都必须获得调用该方法的对象的锁才能执行**，否则线程会阻塞，方法一旦执行，就独占该锁，直到该方法返回才释放锁，后面被阻塞的线程才能获得这个锁，继续执行。
>
> - 缺点：如果将一个大的方法申明为synchronized 将会影响效率





------

#### 互斥锁

1. 对象互斥锁———**保证共享数据的完整性**
2. 两种同步方法方式，锁在**this对象**
3. 关键字**<u>synchronized</u>**来与对象互斥锁联系。
4. 非静态同步方法的锁可以是**this**，也可以是其他对象（要求是同一个对象）
5. 静态同步方法的锁为当前类本身（`当前类.class`）

```java
public void f1(){
	synchronized(this/obj){	//this对象或者其他对象
		//代码块内容
	}
}

//静态方法
public static void f2(){
	synchronized (类名.class) {	//锁在当前类本身
	
	}
}
```



------

#### 线程死锁

> 多线程各自占有一些共享资源，并且互相等待其他线程占有的资源才能运行，而导致两个或者多个线程都在等待对方释放资源，都停止执行的情形。

> 某一个同步块同时拥有”两个以上对象的锁“时，就可能会发生”死锁“的问题。

![image-20230426200532050](https://s2.loli.net/2023/10/16/JUyTwFG68opcr1x.png)



------

#### 释放锁

##### 释放锁的情况

> 1. 同步方法，同步代码块执行结束
> 2. 遇到`break`，`return`
> 3. 遇到异常或Error
> 4. 执行了 `wait()` 方法，线程暂停，并释放锁

- sleep，yield 不会释放锁

- 线程执行**同步代码块**时，其他线程调用了该线程的`suspend()`方法将该线程**挂起**，该线程**不会释放锁**。

- 应尽量避免使用 `suspend()` 和 `resume()`  来控制线程，早已过时

  

------

## 网络多线程

#### 概念

------

##### ip地址

- ip对应ipv4，四个字节，一个字节的范围是 0~255，点分十进制。
- ip地址=网络地址 + 主机地址
- ipv6是用于替代的下一代IP协议，使用128位表示一个地址，16个字节，长度是v4的四倍，

------

##### 域名和端口

- ip地址的映射
- ![image-20230503134510138](https://s2.loli.net/2023/10/16/Cp6YMuvjbWhFTqS.png)
- 在网络开发中，不要使用0-1024的端口，名花有主

------

##### 网络通信协议

> 数据的组织形式，就是协议

![image-20230503135740023](https://s2.loli.net/2023/10/16/ZPKNM3OIiYEhaBw.png)

 ![image-20230503140131356](https://s2.loli.net/2023/10/16/M3hOAEcwLjebWXo.png)

------

##### TCP和UDP

![image-20230503140843547](https://s2.loli.net/2023/10/16/GiPhEvWXx3BnsZy.png)

------

##### InetAddress类

```java
//获取本机的InetAddress对象
InetAddress host1 = InetAddress.getLocalHost();
System.out.println(host1);
//输出指定的主机名字的InetAddress对象
InetAddress host2 = InetAddress.getByName("xoliu1");
System.out.println(host2);
//根据域名获取对象
InetAddress host3 = InetAddress.getByName("www.baidu.com");
System.out.println(host3);
//通过对象获取对应ip地址。
System.out.println(host3.getHostAddress());
//通关过对象返回主机名/域名
System.out.println(host3.getHostName());
```

------

##### Socket

1. 通讯的两端都要有**套接字**（socket），是两台机器间通信的端点。
2. 网络通信其实就是Socket间的通信（TCP编程和UDP编程）
3. Socket允许程序把网络连接当成一个流，数据在两个Socket之间通过**IO**传输。
4. 一般主动发起通信的应用程序属于**客户端**，等待通信请求的为**服务端**
5. ![image-20230503142756660](https://s2.loli.net/2023/10/16/LZ2z1aPgy3fKmjp.png)

------

#### TCP编程

> 当客户端连接到服务端后，实际上客户端也是通过一个端口和服务端进行通讯的，这个端口是TCP/IP来分配的

- ------

-   客户端


```java
public class cilent {
    public static void main(String[] args) throws IOException {
        //1.生成一个Socket对象，连接服务端的接口
        //new Socket(ip地址,端口)
        //下行代码意思是连接本机的9999端口
        Socket socket = new Socket(InetAddress.getLocalHost(),9999);
        //2.连接上后，生成Socket
        // 通过socket.getOutStream()的输出流写入数据到数据通道
        //生成和该通道绑定的输出流对象
        OutputStream socketOutputStream = socket.getOutputStream();
        socketOutputStream.write("hello,world".getBytes());
        //一定记得关闭socket和输出流对象
        socketOutputStream.close();
        socket.close();;
    }
}
```

- 服务端

  ```java
  public class server {
      public static void main(String[] args) throws IOException {
          //1.建立ServerSocket端口
          //细节：要求本机的该端口没有被其他服务监听
          ServerSocket serverSocket = new ServerSocket(9999);
          //2.当没有客户端连接该端口时，程序会堵塞，等待连接
          //如果有客户端连接，就会返回一个Socket对象，程序继续
          Socket socket = serverSocket.accept();
          //3.通过getInputStream()得到输入流对象
          InputStream socketInputStream = socket.getInputStream();
          int readlen = 0;
          byte[] buf = new byte[1024];
          while((readlen = socketInputStream.read(buf)) != -1){
              System.out.println(new String(buf,0,readlen));
          }
          //关闭
          socketInputStream.close();
          socket.close();
      }
  }
  ```

tips:

- 设置**写入的结束标记**，即

```java
socket.shutdownOutput();
```

- 如果使用字符流，需要**手动刷新**，否则数据不会写入数据通道

------

##### 网络上传图片

```java
public class cilent {
    public static void main(String[] args) throws IOException {

        Socket socket = new Socket(InetAddress.getLocalHost(),9999);
        OutputStream out = socket.getOutputStream();
		//得到通道输出流
        FileInputStream in = new FileInputStream("D:\\pic.jpg");
        byte[] bytes = new byte[1024];
        int readlen = 0;
        while((readlen = in.read(bytes)) != -1){
            out.write(bytes,0,readlen);
        }
     //   socket.shutdownOutput();
        OutputStream socketOutputStream = socket.getOutputStream();
        socketOutputStream.write("hello,world".getBytes());
        //一定记得关闭socket和输出流对象
        in.close();
        socket.close();;
        out.close();
    }
}
```

```java
public class server {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(9999);
        Socket socket = serverSocket.accept();

        InputStream socketInputStream = socket.getInputStream();
		//得到通道输入流
        FileOutputStream out = new FileOutputStream("A:\\xoliu1111.jpg");


        int readlen = 0;
        byte[] buf = new byte[1024];
        while((readlen = socketInputStream.read(buf)) != -1){
            out.write(buf,0,readlen);
        }
        //关闭
        socketInputStream.close();
        out.close();
        socket.close();
    }
}
```

------

##### 通过TCP给另一台主机上传文件

```java
public class sender01 {
    public static void main(String[] args) throws IOException {
        String path = "A:\\xoliu1111.jpg";
        FileInputStream fileInputStream = new FileInputStream(path);
        Socket socket = new Socket(InetAddress.getLocalHost(), 9837);
        // new Socket(目标ip地址，发送主机的端口编号)
        OutputStream out = socket.getOutputStream();
        int readlen = 0;
        byte[] bytes = new byte[1024];
        while ((readlen = fileInputStream.read(bytes)) != -1){
            out.write(bytes, 0, readlen);
        }
        fileInputStream.close();
        out.close();
        socket.close();
    }
}
```

```java
public class recevier01 {
    public static void main(String[] args) throws IOException {
        String download_Path = "D:\\data.jpg";
        FileOutputStream fileOutputStream = new FileOutputStream(download_Path);
 		//这里先新建Seversocket接受发送的包，然后用socket接受
        ServerSocket serverSocket = new ServerSocket(9837);
        //返回形式为Socket类型
        Socket socket = serverSocket.accept();
        InputStream in = socket.getInputStream();
        byte[] bytes = new byte[1024];
        int readlen = 0;
        while ((readlen = in.read(bytes)) != -1) {
            fileOutputStream.write(bytes, 0, readlen);
        }
        socket.close();
        serverSocket.close();
        fileOutputStream.close();
        in.close();

    }
}
```





------

##### netstat指令

1. netstat - an 可以查看当前主机网络情况，**端口监听**和**网络连接**
2. netstat -an | more 可以分页显示

------

#### UDP编程

![image-20230503170506743](https://s2.loli.net/2023/10/16/r6tZnmiWOC3f1Pe.png)

1. 没有明确的服务端和客户端，演变成数据的发送端和接收端

2. 接受和发送数据通过 **DatagramSocket**对象完成

3. 将数据封装到**DatagramPacket** 对象/装包

4. 当接收到 datagrampacket对象时，需要进行**拆包**和**取出数据**

5. **DatagramSocket** 可以**指定在哪个端口接收数据**。

   ##### 基本流程

> ![image-20230503170447257](https://s2.loli.net/2023/10/16/xzadNiYMnPBKSeL.png)
>

![image-20230503172447978](https://s2.loli.net/2023/10/16/ZmMWFS89H3hUv1L.png)

##### 发送端

```java
public class sender {
    public static void main(String[] args) throws IOException {
        //1.先创建DatagramSocket对象准备发送
        DatagramSocket socket = new DatagramSocket(8965);
        //这里，发送端的端口最好不要和接收端的端口一样

        //2.将数据封装到packet对象中
        //发送的packet对象需要写入主机IP和端口
        //或者getLocalHost()
        DatagramPacket sender = new DatagramPacket("傻逼樊光辉！".getBytes(), "傻逼樊光辉！".getBytes().length, InetAddress.getByName("192.168.1.62"),6666);
        socket.send(sender);

        //关闭资源
        socket.close();
        System.out.println("发送端已完成");
    }
}
```

##### 接收端

```java
public class receiver {
    public static void main(String[] args) throws IOException {
        DatagramSocket socket = new DatagramSocket(6666);

        //创建接收对象
        byte[] buf = new byte[1024];
        //一个数据包最大64k
        DatagramPacket receiver = new DatagramPacket(buf, buf.length);
        //调用接收方法,将通过网络传输的Packet对象填充到我这里的receiver
        socket.receive(receiver);
        //一旦有数据包传输到该socket对应的端口，即6666时，就会生效，否则处于堵塞等待状态
        //数据将会传入packet对象receiver中
        int length = receiver.getLength();//显示实际收到的数据字节长度
        byte[] data = receiver.getData();//返回接受的数据
        System.out.println(new String(data,0,length));
        //记得关闭
        socket.close();
        System.out.println("接收端已完成");
    }
}
```



------

## 反射



- 传统：new一个类的引用路径

![image-20230505211124528](https://s2.loli.net/2023/10/16/WTGV4R1D7UxsNJX.png)

![image-20230505211326637](https://s2.loli.net/2023/10/16/LtEsrJFzHumMij8.png)

------

### 反射入门

```java
String path = "反射.入门.cat";	//类的引用路径
String method = "hi";		   //方法名
//1.加载类，返回路径path所对应的Class类型对象aclass
Class<?> aClass = Class.forName(path);
//2.获取aclass对象对应的对象实例
// Class.newInstance()  返回对象实例
Object obj = aClass.newInstance();
//obj 的运行类型是Cat类(可以进行强转)
//此时得到该类
//我们不知道调用哪个方法，只知道调用method方法，所以
//3. 通过CLass对象得到类的方法
//Class.getMethod(String method)返回Class类的method方法
//在反射中，可以把方法视为对象，正所谓：“万物皆对象”
Method method1 = aClass.getMethod(method);
//通过返回的Method类型的对象，来调用这个方法
method1.invoke(obj);

```

1. `Class.forName(String path);`      返回path对应的Class对象
2. `Class.newInstance()`  返回Class对应的对象实例
3. `aClass.getMethod(method)`     得到该类的某种方法对象
4. `method1.invoke(obj)`  Method类对象实现方法，括号内填Class对应的对象实例



------

#### 反射机制原理

##### **<u>反射就是把java类中的各种成分映射成一个个的Java对象</u>**

##### <u>**在反射中，可以把方法，成员变量和方法视为对象，正所谓：“==万物皆对象==”**</u>

1.    反射机制允许程序在**执行期**借助 ReflectionAPI取得**任何类**的内部信息（比如成员变量，构造器，成员方法等），并且能操作对象的属性和方法。
2.    加载完类之后，堆中会产生一个**Class类型的对象**。（<u>一个类只有一个Class对象</u>），这个对象包括了**该类的完整结构信息**，通过这个对象得到类的结构，这个Class对象就像一面镜子，透过镜子可以看到类的结构，所以称为反射。
3.    Class对象的由来是==**将class文件读入内存**==，并为之创建一个**Class对象**
4.    ![image-20230505214716238](https://s2.loli.net/2023/10/16/c2zySqCNViwsx3J.png)

------

##### 反射机制可以完成什么？

> ![image-20230506125339936](https://s2.loli.net/2023/10/16/Hg4atc2zwlIKBVY.png)



------

#### 反射相关类

##### 成员变量

```java
//*Class.getField(String name) 返回name对应的成员变量
//*getField 不能得到私有属性
Field age = aClass.getField("age");
System.out.println(age);           
//输出public int 反射.入门.cat.age
System.out.println(age.get(obj));  
//输出 age 的值 1
```

##### 构造器

```java
Constructor<?> constructor = aClass.getConstructor();
System.out.println(constructor);
//输出public 反射.入门.cat()
Constructor<?> constructor1 = aClass.getConstructor(String.class);
//*这里的String.class指的是String类所对应的Class对象
//*这里会返回带有String形参的构造器对象，这个构造器对象可以调用方法
System.out.println(constructor1);
//输出public 反射.入门.cat(java.lang.String)
```



------

#### 反射调用优化

> 反射的调用相对传统方法耗时很长，可以**关闭访问检查**来优化

1. Method和Field、Constructor对象都有 `setAccessible（）`方法
2. `setAccessible`  作用是==**启动和禁用访问安全检查**==的开关
3. 括号内如果填 <u>true</u> ,反射的对象就会**在使用时取消访问检查**，提高反射效率；参数值为false ，则会执行访问检查

- **经过测试，快了那么一丢丢（真的就一丢丢）**

------

### Class类

#### Class类分析

> 1. Class不是new的，而是系统自动创建的
> 2. *对于某个类的**Class类对象**，在<u>内存</u>中**只有一份**，因为==**类只加载一次**==
> 3. 每个类的实例都会记得自己是由哪个Class实例所生成
> 4. CLass对象通过api可以得到**一个类的完整结构**
> 5. Class对象存在==<u>**堆**</u>==中
> 6. 类的字节码二进制数据，是放在==方法区==的

#### Class类常用方法

| **Field[] getFields()**                      | 返回一个包含Field对象的[数组](https://so.csdn.net/so/search?q=数组&spm=1001.2101.3001.7020)，存放该类或接口的所有可访问公共属性（含继承的公共属性） |
| -------------------------------------------- | ------------------------------------------------------------ |
| **Field[] getDeclaredFields()**              | 返回一个包含Field对象的数组，存放该类或接口的所有属性（不含继承的属性）。 |
| **Field getField(String name)**              | 返回一个指定公共属性名的Field对象。                          |
| **Method[] getMethods()**                    | 返回一个包含Method对象的数组，存放该类或接口的所有可访问公共方法（含继承的公共方法）。 |
| **Method[] getDeclaredMethods()**            | 返回一个包含Method对象的数组，存放该类或接口的所有方法（不含继承的方法）。 |
| **Constructor[] getConstructors()**          | 返回一个包含Constructor对象的数组，存放该类的所有公共构造方法。 |
| **Constructor getConstructor(Class[] args)** | 返回一个指定参数列表的Constructor对象。                      |
| **Class[] getInterfaces()**                  | 返回一个包含Class对象的数组，存放该类或接口实现的接口。      |
| **T newInstance()**                          | 使用无参构造方法创建该类的一个新实例。                       |
| **String getName()**                         | 以String的形式返回该类（类、接口、数组类、基本类型或void）的完整名。 |
| **getClassLoader()**                         | 返回该Class对象对应的类的类加载器。                          |
| **getSuperClass()**                          | 返回某子类所对应的直接父类所对应的Class对象                  |
|                                              |                                                              |
|                                              |                                                              |
|                                              |                                                              |

------

#### 获取Class类对象

##### ①已知全类名，且该类在类路径下

> 通过==Class.forName(String Classpath)==来获取

多用于**配置文件，读取类全路径**

##### ②已知具体的类

> 通过 ==类名.class== 来获取，此方法最为<u>安全可靠，性能最高</u>

多用于**参数传递**

##### ③已有该类的对象实例

> 通过==对象.getClass()== 来获取

##### ④通过类加载器来获取

> ![image-20230506165605725](https://s2.loli.net/2023/10/16/C2FO4m79Da5lVUI.png)

##### ⑤基本数据类型获取

> 通过 ==基本数据.class== 获取

##### ⑥基本数据类型对应的封装类获取

> 通过 ==封装类.TYPE== 获取
>



------

#### 哪些类型有Class对象

![image-20230506165753974](https://s2.loli.net/2023/10/16/tOBLrCjAuMFYElp.png)

------

### 类的加载

- 静态加载：**编译时**加载相关的类，如果没有该类则报错，依赖性太强
- 动态加载：**运行时**加载需要的类，如果运行时不用该类，及时不存在该类，也不报错，降低了依赖性。

------

#### 类加载时机

| **new对象**                | **静态加载**     |
| -------------------------- | ---------------- |
| **子类加载，父类也被加载** | **静态加载**     |
| **调用类的静态成员**       | **静态加载**     |
| **通过反射**               | **==动态==加载** |

------

#### 类加载流程

![image-20230506175209874](https://s2.loli.net/2023/10/16/7LFhT1kIwvRQqEH.png)

##### 连接阶段：

![image-20230506175755591](https://s2.loli.net/2023/10/16/eq8olMNmkwfJvd4.png)

![image-20230506175739249](https://s2.loli.net/2023/10/16/Igv5eunlMjEzTtG.png)

------

### 类的结构获取

以下是简单应用：

```java
String path = "反射.入门.cat";
//首先获取Class对象
Class<?> cls = Class.forName(path);
//得到详细类名
System.out.println(cls.getName());
//得到简单类名
System.out.println(cls.getSimpleName());
//得到public变量，包括本类以及父类的成员属性数组
Field[] fields = cls.getFields();
for (Field i: fields) {
    System.out.print(i.getName() + " ");//要加getName得到名字
}
//如果想要获取所有属性（包括父类的），使用getDeclaredFields()  //不要少了s
//父类的父类都可以获取
Field[] declaredField = cls.getDeclaredFields();
//获取方法，构造器的也一样,改成Methods即可
//返回的构造器不含父类的
//Package形式返回包的信息
System.out.println(cls.getPackage());
//以Class形式返回父类信息
Class<?> superclass = cls.getSuperclass();
//以Class[]形式返回接口信息
Class<?>[] interfaces = cls.getInterfaces();
//返回注解信息
Annotation[] annotations = cls.getAnnotations();
```

------

#### 获取Class属性的部分api

- 属性对应的Class类对象.getModifiers()

> 该方法以==int形式==返回**该属性的修饰符**。可用于属性，方法和构造器
>
> ***多种修饰符组合时，返回<u>相加</u>结果**
>
> | public | private | protected | static | final |
> | ------ | ------- | --------- | ------ | ----- |
> | 1      | 2       | 4         | 8      | 16    |



- 属性对应的Class类对象.getType()

> 该方法以<u>**Class形式**</u>返回该属性的**数据类型**



- 属性对应的Class类对象.getName()

> 返回该属性的名字，也可用于方法和构造器



- 方法对应的Class类对象.getReturnType()

> 返回该方法的**返回类型**



- 方法对应的Class类对象.getparameterTypes()

> 返回该方法的形参类型数组，也可用于构造器。



------

### 通过反射访问类

![image-20230508130818356](https://s2.loli.net/2023/10/16/UlCfMPzS5WGOBt4.png)

```java
String path = "反射.入门.cat";
Class<?> cls = Class.forName(path);
//无参
Object o = cls.newInstance();
//有参
/** 利用String构造器，括号内填形参的类型对应的Class对象*/
Constructor<?> constructor = cls.getConstructor(String.class);
//然后用返回的构造器构造对象
Object o1 = constructor.newInstance("小6");
/**只能用这个方法构造出public修饰的构造器
 * 用getDeclaredConstructor（）+ 暴破，即可获得private的构造器
 */
Constructor<?> constructor1 = cls.getDeclaredConstructor(int.class, String.class);
constructor1.setAccessible(true);
//这个就是【暴破】，破坏封装性，这样就可以访问private构造器了
Object o2 = constructor1.newInstance(123, ":XiaoMiao");
```

------

#### 【暴破】

`属性对应的Class对象.setAccessible(true)` 即为暴破



#### 通过反射访问类中的<u>私有</u>成员

```java
Field age = cls.getDeclaredField("age");
//set构造，利用 filed.set(Class aclass, int num)
//将aclass中field对应的属性修改为num
age.set(o, 80);
System.out.println(age.get(o));//获取age的值
//私有属性
Field privateAge = o.getDeclaredField("privateAge");
//私有属性开始暴破
privateAge.setAccessible(true);
privateAge.set(o, 1);
//静态属性
Field key = cls.getDeclaredField("key");
key.set(null, 9);
System.out.println(key.get(null));
//只有静态属性可以这样用,因为其属于所有类
```

#### 通过反射访问类中的方法

用法同上

调用方法：

> **method.invoke(o,形参列表)**

- 在反射中，如果方法有返回值，统一返回<u>*Object*</u>，但是其**运行类型还是与方法的返回类型保持一致**














------

------

------

## 设计模式

### 单例模式

**==单例模式，即只创建一个实例==**

#### 饿汉式

如何保障我们只创建唯一的对象？

①首先**将构造器私有化**，这样我们在别的类中无权限new对象

②将**这个类的特征信息私有化**，这样在别的类中也无法改变这个类的属性

③因为属性私有化，所以我们只能**在本类创建对象**，所以需要在本类new一个对象，并初始化属性，而且这个对象我们希望在每一个类都可以使用而且唯一，所以**这个对象也是一个<u>静态</u>变量**，加static。

④我们再在**这个类里边创建一个公共静态方法（getInstance）去返回这个对象**，这样我们在哪里都可以访问这个唯一的对象。这里需要注意，**返回类型是这个类**

那么我们在别的类访问这个对象时，就不再需要new这个类，而是定义编译类型变量，等号右边是类名+方法名（返回的东西就是那个唯一的对象）

![image-20230402195553225](https://s2.loli.net/2023/10/16/mtYb62FWiUoOHZl.png)

tip：因为我们想要访问这个对象，跟那些库函数一样，即使没有定义，这个静态属性就已经随着类的加载而诞生了，所以叫饿汉。



