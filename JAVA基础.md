# JAVA基础:

java特性:

​	跨平台运行

> java源代码通过java编译器后生成虚拟机代码 此代码不对应任何特定处理器,java虚拟机将虚拟机代码编译后生成处理器专用代码 实现了系统结构的中立性

​	垃圾收集机制

​	多线程

​	动态分配内存

​	取消全局变量定义,通过公用静态变两完成全局变量的功能,使用try-catch-finallly异常处理语句

​	不使用宏定义 使用final定义常量

​	属于半解释半编译语言

1. ### 运行机制

   1. 通过类装载器完成字节码的装载,将运行程序所设计的所有代码都装载
   2. 通过字节码检验其对字节码进行安全性检查
   3. 字节码的翻译和执行,将字节码通过代码生成器反义词适用于系统的机器前码,在给硬件执行.(高效)/解释器将字节码翻译成机器码由及时运行部件立即将机器码送至硬件执行.(常规)

2. ### 环境

   ​	java虚拟机(JVM):可运行java代码的假想机器 提供一个基于抽象规格描述的计算机模型

   ​	JVM定义了控制Java代码解释,执行和具体实现的五种规格

      	1. JVM指令系统:java指令由操作码和操作数两部分组成
                 	2. JVM寄存器:JVM设置了4种常用的寄存器:pc程序计数器,optop操作数栈顶指针,frame当前执行环境指针,vars指向当前执行环境中第一个局部变量的指针
                 	3. JVM堆栈结构:当JVM得到一个java字节码应用程序便为该代码中类的每一个方法创建一个堆栈框架,以保存该方法的状态信息,每个堆栈框架包括局部变量,执行环境,操作数栈三类信息
                 	4. JVM碎片回收堆:java中除new语句外无其他方法对对象申请和释放内存(此工作由java运行系统执行) 运行java运行系统设计者自行决定碎片回收方法.
           	5. JVM存储区:常量缓冲池(存储类名称,方法,字段名称,串常量)和方法区(存储java方法字节码)

3. ### 平台

   完整的JAVA平台包括五个部分:JAVA应用程序接口(API) JAVA基本条件类(基本类和扩展类) JAVA虚拟机(jVM) 适配器 实际计算机 

Java符号集:

Java采用Unicode符号集,将8位的ASCII字符集扩展到16位(可输入汉字字符).

语言符号:标识符,关键字,常量,运算符,分隔符.

标识符:以字母,_,$开头,后字符可接数字,英文字母和十六进制大雨0XC0的unicode码 且关键字不能作为普通标识符.

关键字:![](/home/htxone/e28691a8b1e81d6d2ffa4d469ab43a2e.jpg)

this关键字：对调用方法的对象的引用。使用this访问与变量同名的实例参数（否则参数被隐藏）

常量: 程序执行过程中固定的值(整型,浮点型,布尔型,字符型,字符串型)

运算符:进行程序运算的符号

分隔符:区分源程序的成分:注释 空白符,普通分隔符.

数据类型 : 

| 类型    | 长度(位) |
| ------- | -------- |
| boolean | 1        |
| byte    | 8        |
| short   | 16       |
| int     | 32       |
| long    | 64       |
| float   | 32       |
| double  | 64       |
| char    | 16       |

强制转换:(数据类型) 变量名

java 的false为-1

bool型不能强转.

变量定义:与C相同.

(Java变量在不同作用域中也不能重名)

常量:5种数据类型都可定义

表达式自动类型提升,但尽量不用(但表达式的值超过操作数值的定义范围时自动将表达式结果的数据类型提升)

运算符:![](/home/htxone/图片/index.jpeg)

字符串运算:使用+来合并两个字符串,使用string类的Equals()来对两个字符串进行判断

java的三元运算符返回值不能是void型（即不能用三元运算符进行void方法分支）

数组定义:数组定义与C不同 java的对象特性使java数组需先定义数组引用然后使用new方法新建数组并将引用赋予.（java可使用动态分配多维数组（第一维已确定情况下））

>```java
>type arrName[]=new type[size];
>type arrName[]={......};
>```
>
>



代码块：java程序中使用{}扩起的代码称为一个代码块

> 代码块添加标签： 
>
> ```
> one: {......}`//标签为one的代码块
> two: {		//标签为two的代码块
> 	three: {....}	//在two代码块中的three代码块
> }
> ```
>
> 

条件语句和循环语句基本上与C相同

java的break语句具有扩展功能：课使用带标记的break语句形成一种goto语句

java的for-each语句可按找严格的顺序从头到尾遍历数组：

```java
for(type itr-var : arrName){......}//itr-var为遍历时将集合的下一元素检索并保留在var中（同arr[i]）但无法通过修改var对数组内元素进行修改
```



>```
>break label；//将程序指针跳转到label标签代码块之后
>```
>
>

输入输出:

`System.out.println()`//输出

`System.in.read()`//读入一个字符

## 字符串类：

构造新字符串：`String newStr = new String("......")`//通过字符串类进行实例化构造

字符串方法：

| 方法                                          | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| boolean equals(String str)                    | 比较两字符串                                                 |
| int length()                                  | 获取字符串长度                                               |
| char charAt(int index)                        | 获取index位的字符                                            |
| int compareTo (String str)                    | 比较字符串，若原字符串小于str则返回小于0的数大于返回大于0的数，相等返回等于 |
| int indexOf(String str)                       | 查找字符串中的子串str 若找到返回第一个索引位 否则返回-1      |
| int lastIndaxOf(String str)                   | 查找子串返回最后一个索引位 未找到返回-1                      |
| String subString(int startIndex,int endIndex) | 截取指定范围内的子串（左闭右开）                             |

字符串‘===’操作判断是否为同一对象

字符串数组：`String arrStr[] = {str1,str2,.....}`

JAVA字符串不可变：java字符串在创建后不可修改 若需要只需新建一个新字符串（旧的由垃圾回收器回收）

##### 命令行参数：

程序执行时在命令行向程序进行传参（使用main函数的String args[]字符数组实现）

在使用命令行数组时 程序需先判断`if(args.length !=0)`

通过按位运算符将字母进行大小写转换：

>```
>ch = (char)((int)ch&65503)	//将小写转换为大写
>ch = (char)((int)ch|32)		//将大写转换为小写
>```
>
>



## 面向对象：

1. ### 类：

   命名空间：java中在命名类时 先从命名空间分配一个名字，命名空间定义一个公告区域 两个类不能在同一个命名空间使用相同的名字

   一系列具有相同属性的对象的抽象。

   使用class定义类，并在定义使指定类的属性（属性参数与方法）

   使用new创建类的实例，使用  **.  **来防卫实例对象的继承类属性值

   构造函数：在对象实例化时将对象类属性值进行初始化（未设置则java自动生成构造函数且都默认初始化为0） 构造函数与类重名 使用构造函数传参初始化（构造函数方法不用加返回状态值）

   >```
   >class a{
   >	a(....){			//a的构造方法
   >		....
   >	}
   >}
   >```
   >
   >

2. ### 对象：

   抽象类的实例化。

   创建：使用类名称和new方法进行创建：

   > `className objectName = new className(parameters);`
   >
   > //第一个classname定义对象的类型，new运算符为对象分配一个类实例的空间。className objectName实际上创建的是一个对象引用，new方法创建一个对象实例并将其引用赋给objectName

   对象副本：对象实例化时都会产生一个相关类参数的对象副本，在对象使用类方法时，类方法中的参数抽象调用该对象的对象副本的值（同this关键字）

   对象方法传参：直接在对象调用类方法时传入指定参数即可

### 垃圾回收与终止器：

​	java垃圾回收系统会自动回收不用的对象，且垃圾回收器会占用时间

​	finalize()方法：在对象被垃圾回收器销毁之前调用确保对象正常地完全终止活动

> finalize()方法需自行定义在类中：
>
> ```
> protected void finalize(){....}//使用protected防止方法被类以外的代码调用
> 
> ```

#### java的参数传递：

java参数传递两种方式：传值调用，引用调用

传值调用：将变量的值传给方法形参，形参和实参不在同一个存储空间中

引用调用：将变量的引用传给形参，形参指向实参存储空间，即对形参操作也是对实参操作。

## java对类成员的访问：

1. ### java的访问指示符：

   成员访问控制指示符：public，private，protected

   当使用public修饰类成员时程序中的然后代码都可访问该成员（全局变量）

   当使用private修饰类成员时仅该类中其他成员可访问该成员

   程序为打包情况下默认访问设置是public

2. 成员声明语句：

   ```
   status type name;		//定义成员参数
   status type nmae(type parameters){......}	//定义成员方法
   ```

3. 非类可访问成员错误阻止方法：

   在类中定义一个检测方法，检测传入索引是否越界 若未越界则返回 否则捕捉错误返回异常信息
   
4. 使用对象参数：

   使用对象参数将把实例化了的对象整体传参（即可在其他方法内调用对象属性 对象参数是引用调用）


### JAVA方法重载：

​	同一个类中定义一个或多个同名方法，且保证每个方法的参数（参数的数量和值类型不同）声明不同，此时通过不同的传参执行不同的方法，这类同名方法为方法重载。

> 方法重载只对传参声明不同有要求 对方法返回值等其他内容不要求
>
> 重载的方法对应工作在编译器中执行。
>
> 重载使java实现单接口多方法的途径之一 支持多态性。

对类的实例构造函数进行重载，在实例化时使用不同的参数声明构造不同的类实例对象。

```java
>对构造函数进行重载 可使通过现有对象构造新的对象 新对象在构造方法内继承原始对象的属性。
>
>```
>class object {
>	object(){	//构造方法
>		....
>	}
>	object(object old){
>		.....//因为进行了引用调用，可获取修改旧对象的属性
>	}
>}
>```
>
>
```

java static关键字

​	在类中设置static类成员后，该成员的属性将在所有被此类创建的对象中进行共享。（即为这些对象间的全局变量） 且在外部代码调用时可不通过某个对象而是直接通过类来对此成员进行访问。

> static成员方法的限制：static方法只能调用类中static对象对其他对象无法进行访问，且static方法中无法使用this引用

​	在类中设置static代码块进行类对象初始化执行方法（在同一个类的第一个对象初始化时执行)在类第一次使用前执行

java嵌套类

​	在java类中可声明嵌套类，且此类只被声明的类所调用（嵌套类的作用域限制在外层类中）嵌套类有权访问私有成员在内的外层类所有成员 但外层类无权访问嵌套类的成员。嵌套类中有带static关键字和不带关键字的两种 其中不带的嵌套类被称之为内部类 它可以向外层类的其他非静态成员一样直接引用。对嵌套类的成员方法在为加static的情况下需要通过实例化对象进行访问

java可变长度变元方法Varargs：

​	可变长度变元有三个句点表示（...）可变长度变元的初始化声明和调用声明必须放在参数列的最后且每个参数列中只能有一个可变长度参数

​	变元方法初始化：

```java
static void vaName(elementType ...name){....}
```

> 将name的可变长度变元初始化 且在重新赋值后原数据删除
>
> varargs变元在重载时可能会对空组产生语义歧义（编译器无法知道应重载哪个方法）

### JAVA类的继承：

1. java使用extends关键字来进行继承操作

```java
class newClass extends oldClass{....}
```

> 父类对象无法访问子类内容 子类算作父类的实例化 java不支持多重继承，一个子类只能继承于一个父类	

2. 成员的访问：

   当类的成员变量被设置成private时 即使是子类也无法获取父类中的private对象，private元素只能在父类中调用。（当需要调用时在父类中洗一个返回相应成员值的访问器方法）

   但是子类中继承了父类的private型对象 只是需要父类的访问器方法进行访问

3. 父类和子类的构造函数：

   父类的构造函数构造对象的父类成员，子类构造函数构造对象的子类成员，两者间的构造分开进行

   super关键字：使用super调用父类构造函数，或者用于访问被子类成员隐藏的父类成员

   在子类的构造函数中使用super（）方法执行父类的构造函数（super（）方法作为子类中的父类构造方法，在父类构造函数存在重载时 super（）方法对应进行父类重载构造函数）当父类构造函数需要传参时 无论子类是否会用到都需要在子类构造函数中使用super将父类的构造参数传给父类。

   构造函数的调用顺序为从根父类开始依次向下层子类调用，所以对于子类的构造函数中，给父类传参的super方法必须方法在第一行 若不使用super方法则默认父类参数为初始化参数

   在子类中使用super.name调用父类被子类所隐藏的成员（效果同在父类中使用this关键字）

4. 通过多层继承来建立类的层次结构

5. 一个类的类型引用变量不能引用其他同级类的类型引用变量

   父类的类引用可以引用子类对象，但引用中所包含的成员只有父类定义的成员

   > ?（但可以通过强制转化进行）

6. 方法重写：当子类中的方法和父类中的方法同名且声明一致时称子类方法重写了父类方法，父类方法将被隐藏。（在子类中用super关键字调用被子类重写了的父类方法）（重写和重载不同，重写要求父子类方法声明完全一致，在子类中父类方法被隐藏，重载要求传参不同，在子类中父类和子类方法同时存在，只是调用时需传递不同的参数）

   重写支持多态性：重写组成java的动态分配概念：对重写方法的调用是在运行时解决而不是在编译时解决。（java根据调用方法时调用此方法的对象所引用的类进行调用方法的选择。即此时为对应类对方法的调用，而与此时对象的类型无关 但对象类型一定是当前引用类的父类（父类能调用子类对象 而子类无法调用父类对象 且调用方法后和子类的重写方法表示相同））

   方法重写机制使一般类课应指定其所有派生类都可以共享的方法 同时允许子类定义这些方法（或这些方法中的一部份的具体体现）

7. 抽象类：创建一个父类 其中只定义一个所有子类所共享的一般形式，成员细节交给子类进行填充 这类父类决定了子类必须执行的方法本质，而不是提供方法的表现形式

   使用abstract类型修饰符来创建抽象方法，抽象方法无内容  父类不用实现 子类必须重写

   ```
   abstract type name(parameter_list);		//定义抽象方法 且无方法主体
   ```

   abstract修饰符只能用于普通方法 无法用于要求要执行的static方法和构造函数。

   包含抽象方法的类必须通过在class声明前添加abstract修饰符将其声明为抽象类（抽象类不定义完整的方法实现方式 所以抽象类无法新建对象（使用new方法新建报错））

   子类继承抽象类时必须实现父类中的所有抽象方法，否则子类也为抽象类 也需要和父类一样的定义方式

   （抽象方法的实现是利用了方法重写的机制）

8. final关键字阻止方法重写和类的继承：

   ```
   final type name(parameter_list){...}	//定义一个不能被子类重写的方法
   ```

   ```
   final class name{.....}		//定义一个无法被继承的类
   ```

   ```
   fianl type name = vlaue			//定义一个被赋初值后不可改值的常量（可被子类调用）
   ```

9. ### object类：

   根类

   | 方法                                          | 操作                                 |
   | --------------------------------------------- | ------------------------------------ |
   | Object clone()                                | 创建一个新的对象和被克隆对象完全相同 |
   | boolean equals(Object objectName)             | 比较两对象是否相等                   |
   | void finalize()                               | 在为使用对象被回收前调用             |
   | Class getClass()                              | 在运行是获取对象的类                 |
   | int hashCode()                                | 返回于调用对象相关的哈希代码         |
   | void notify()                                 | 继续执行等待调用对象的线程           |
   | void notify All()                             | 继续执行等待调用对象的所有线程       |
   | String toString()                             | 反回描述对象的字符串                 |
   | void wait()                                   | 等待另一个线程的执行                 |
   | void wait(long milliseconds)                  | 等待方法添加等待时间参数             |
   | void wait(long milliseconds, int nanoseconds) |                                      |
   |                                               |                                      |

   其中getClass() notify() notifyAll() wait()方法被定义为final类

### java包和接口：

1. ### 包：

   通过包实现将程序段组织起来 

   包提供把相关程序段组织成一个单元的机制 在包中定义的类必须通过其包名进行访问

   包参与java的访问控制机制 为类提供一种能被封装的方式

   在包内定义类名时 包名将被附在类名上 避免了其他包中相同名类造成的冲突。

   java中所有类都属于某一个包 当未中鼎package语句时默认使用全局包

   包名区分大小写

   可使用嵌套包 在打开包时使用`package a.b.c.......n;`打开包（在目录/a/b/c/....../n下）

   包的寻找：java运行时系统使用当前运行目录作为起点 若类文件在当前目录中（包括子目录）则可直接找到包 货主额设置classpath环境变量指定一个或多个目录路径。

   包和成员访问：类成员访问权限：

   ​				![](C:\Users\79931\Downloads\18ba5f99dd672cadd0c6ad7ebbf8a961.jpg)

   默认访问权：允许包中的所有成员访问

   使用public 关键子确保类成员在包外代码可调用。

   （如果包外代码需要调用，类构造函数需要被声明为public型）

   使用import进行包的导入

   ```
   import pkg.classname; //调用pkg包中的class类
   inport pkg.*		//调用包中的所有类
   ```

   （若不导入包则需要通过包名来导入）

   java类库：java定义了所有程序都可以使用的大量标准类（java API） 类存放在包中 包的顶层是java 

   java子包：

   | 子包        | 描述                                 |
   | ----------- | ------------------------------------ |
   | java.lang   | 包含大量通用类                       |
   | java.io     | 包含I/O类                            |
   | java.net    | 包含支持联网的类                     |
   | java.applet | 包含创建applets的类                  |
   | java.awt    | 包含支持Abstract window Toolkit 的类 |

   > System类包含在java.lang中其自然导入java程序中

2. ### 接口：

   （上下关系明确时使用抽象类继承，不明确时使用接口，接口可看作抽象类的特例 但运行一个类继承于多个接口但只能继承于一个父类）

   用于实现不同类的共同行为

   使用关键字 interface 将类接口和实现方式完全分开

   一个接口可由任意数量个类实现，一个类可以实现任意数量的接口

    类为接口描述的方法提供实现方式，每一个类蜘蛛决定其实现方式的细节 即两个类可能以不同的方式实现同一个接口 
   
   接口的一般形式：
   
   ```
   access interface name {
   	ret-type method-name1(param-list);
   	ret-type method-name2(param-list);
   	type var1 = value;
   	type var2 = value;
   	......
   	ret-type method-nameN(param-list);
	type varN = value;
   }
//access为public或无 当不包含访问指示符时，执行默认访问方式 接口仅对其所在包其他成员可用 当接口被声明为public时 可被任何其他代码使用（当一个接口被定义为public时 必须位于同名文件中）
   ```

   方法为抽象方法，包含接口的每个类都必须实现全部方法 接口中方法显式声明为public abstract(默认)

   接口声明变量不是实例变量 其被显式声明为public static final（默认） 且必须被初始化 为常量。

   接口的实现：
   
   在类定义中包含implements关键字 再创建由接口定义的方法 
   
   ```
classname extends superclass implements interface{
   	....
}
   ```

   若要实现多个接口 可使用逗号分开

   实现接口的方法必须被定义为public型 且实现方法类型必须和接口定义类型相同

   实现接口的类方法可多于但不能少于接口定义的方法数（可以在类中定义附加方法）
   
   如果一个类包含接口但没完全实现接口定义的方法 则此类必须声明为抽象类 
   
   接口引用：创建接口引用变量 此变量可以引用任何实现其接口的对象 当通过接口引用调用一个对象上的方法时 将会执行对象实现的方法版本 类似于一个只拥有接口定义方法的超类引用子类对象
   
   ```
   interface_name objectRecommend;	//接口引用对象创建
   ```
   
   接口引用变量不能访问除定义外其他实现类成员  且只能对同一接口实现类对象进行引用
   
   接口变量：使用接口变量（实际上是常量）对接口实现类中成员作特殊值或限制 对于接口变量可直接进行变量名进行引用（在类添加implements后）
   
   接口扩展：
   
   使用extends关键字对接口进行扩展操作 扩展接口方法与继承类语法相同 当一个类要实现继承了其他接口的接口时 其要对所有有关接口进行方法实现否则为一个抽象类

### 异常处理：

1.  定义一个可以在错误发生时自动执行的代码块来形成错误处理 

2. java为常见程序错误定义了标准异常 求java的api库可扩展异常的使用

3. 异常的层次结构

   java中 所有的异常都有类来表示 所有的异常类都从一个名为Throwable的类派生出来 当程序中发生一个异常时 会生成某种异常类的对象

   程序活动导致的错误由Exception子类表示

4. 异常处理基础：
   异常处理由5个关键字来进行管理 try，catch，throw，throws，finally 形成互相关联的子系统 

   异常监测程序语句包含在try代码块中 try中出现异常 将thrown该异常 使用catch进行异常捕获处理 如果需要手动抛出异常 则使用throw关键字 在某些情况下从一个方法抛出的异常必须用一个throws语句来指定为异常 任何try代码块退出时必须被执行的代码放在finally代码块中

5. try/catch异常获取

   ```
   try {
   	.....//the code which will block;
   }
   catch (ExcepType1 exob){
   // handler for ExcepType1
   }
   catch (ExcepType2 exob) {
   //handler for ExcepType2
   }		//ExcepType 为异常发生类型 exOb接收异常抛出的值
   //try中出现异常并抛出后 异常后的代码不会被执行 try同样监视try
   //中调用的方法 若方法未被其他try中方法进行捕获这会执行catch
   //try和catch之间不能插入其他语句
   
   ```

   程序再处理完异常后 异常将被删去

6. 捕获子类异常：
   因为所有的异常都属于超类Throwable的子类对象 所以可用对Throwable类对象错误的捕获来捕获所有异常（子类错误可由超类catch捕捉） 如果希望先捕获可捕获的子类异常 需先将子类异常的catch语句放在超类catch语句前 否则超类捕获所有异常而子类异常捕获语句无法进行

7. try嵌套：

   将try代码嵌入另一个try代码块中 如果内部try的错误未被捕捉 则可由外部try代码进行捕捉 使用内部try捕捉轻微错误 外部try捕捉致命错误

8. 抛出异常：

   ```
   throw new ErrorTypeClass();//抛出一个异常类型为ErrorTypeClass的错误对象(此类型必须是Throwable的子类)
   ```

9. 重抛异常：

   将捕获了的异常从catch中重新抛出使外部catch捕获 为了运行于多重程序访问异常 （当一个异常需要多个异常处理程序进行分块处理时） 

   > 抛出后由紧接则课获取的catch语句执行 和内外结构无关
   >
   > 且抛出的为当前获取的异常

10. throwable类

    | Throwable类方法                          | 描述                                                         |
    | ---------------------------------------- | ------------------------------------------------------------ |
    | Throwable fillInStackTrace()             | 返回一个包含完整堆栈trace的Throwable对象该对象可被重新抛出   |
    | String getLocalizedMessage()             | 返回异常的本地描述                                           |
    | String getMessage()                      | 返回异常的描述                                               |
    | void printStackTrace()                   | 显示堆栈跟踪                                                 |
    | void printStackTrace(printSteam steam)   | 将堆栈跟着传送到指定流                                       |
    | void printStackTrace(PrintWriter stream) | 将堆栈跟踪传送到指定流                                       |
    | String toString()                        | 反回一个包含异常描述的String对象 当输出一个对象时 println调用此方法 |
    |                                          |                                                              |

11. finally异常退出：

    使用finally执行异常退出（try无论正常退出还是异常退出 都会执行finally代码块）(try中return是跳出try代码块)

    ```
    try{
    .....
    }
    catch{
    .....
    }
    finally{
    .....
    }
    ```

12. throws 再某些情况下 如果方法产生无法处理的异常 这必须在throws语句中声明该异常




# I/O

## 字节流类：

1. 顶端类：InputStream OutStream

   | 字节流类              | 意义                                     |
   | --------------------- | ---------------------------------------- |
   | BufferedInputStream   | 输入流缓冲                               |
   | BufferedOutputStream  | 输出流缓冲                               |
   | ByteArrayInputStream  | 从子节数组中读取输入流                   |
   | ByteArrayOutputStream | 写入字节数组的输出流                     |
   | DataInputStream       | 包含用于读取Java标准数据类型方法的输入流 |

   InputStream定义方法

   | 方法                                        | 表示                                                         |
   | ------------------------------------------- | ------------------------------------------------------------ |
   | int available                               | 赶回当前可读取的输入字节数                                   |
   | void close()                                | 关闭输入流 而且任何读取尝试将生成一个IOException             |
   | void mark(int numB)                         | 在输入流的当前点放置一个标记 在读取numBytes数量的字节之前保持有效 |
   | boolean markSupported()                     | 如果被调用流支持mark()/reset() 则返回true                    |
   | int read()                                  | 返回一个整数代表下一个输入的有效字节 返回-1时表示到达文件末尾 |
   | int read(byte buffer[])                     | 尝试读取buffer.length数量的字节到缓存 并返回实际成功读取的字节数 返回-1表示到达文件末尾 |
   | int read(byte buffer[],int offset,int numB) | 尝试读取numBytes 数量的字节到缓存中以buffer[offset]开始的位置 并返回实际成功读取的字节数 返回-1时表示到达文件末尾 |
   | void reset()                                | 将输入指针重新改为原来设置的标记                             |
   | long skip(long numB)                        | 体哦啊个numBytes个数量的输入字节 返回实际被跳过的字节数      |

   Output Stream定义的方法

   | 方法              | 表示                                           |
   | ----------------- | ---------------------------------------------- |
   | void close()      | 关闭输出流 而且任何写尝试将产生一个IOException |
   | void flush()      | 完成输入状态 时任何缓冲清空                    |
   | void write(int b) | 向输入流写入单个字节                           |
   |                   |                                                |

   

## 字符流类：

1. 顶端类：Reader Writer

标准输出流： System.out 

标准输入流：System.in

控制台read()方法（使用System.in.read()进行）：

```java
int read() throws IOExpection;
int read(byte data[]) throws IOExpection;
int read(byte data[],int start,int max) throws IOExpection;
```

#### 文件写入写出：

读文件：

通过FileInputStream对象打开一个可读文件

```java
FileInputStream(String fileName) throws FileNotFoundExpection
```

使用read()对文件进行单个字符的依次读取 当到达文件尾时read()返回-1 处理完文件之后使用close()来进行文件关闭

```java
void close() throws IOExpection;
```

写文件：

使用FileOutputStream 对象来对文件进行写入

```java
FileOutputStream(String FileName) throws FileNotFoundExpection;//不存在则新建 存在则覆盖
FileOutputStream(String fileName,boolean append) throws FileNotFoundExpection;//如果append为true则在已出现文件尾进行添加
```

使用write()来进行文件写入

```java
void write(int byteval) throws IOExpection;
```

向文件中写入byteval指定字节

但其实在写文件过程中不会立刻将字节直接写入文件而是将其存在缓存中等到存在相当大小的数据块可一次性写入为止 如果需要让数据直接写入实际物理设备使用flush()方法

```java
void flush() throws IOExpection
```

当文件写入完毕调用close()方法关闭文件并保证将缓存区中数据全部写入文件

```java
void close() throws IOExpection
```



# 多线程

多线程程序可以包含两个或多个可同时运行的部分 这种程序的每一个部分被称之为多线程

多任务：分为基于过程与基于线程的多任务 基于过程多任务是运行计算机同时运行两个或多个程序的功能 基于线程的多任务中线程是最小可分配单元 即多线程允许一个程序一次运行多个任务

线程状态：运行，就绪，挂起（运行时），继续执行，阻塞（运行时等待资源），终止（运行完毕）

同步化：允许线程以某种定义完好的方式并列执行

#### Thread类和Runnable接口

java的多线程系统建立在Thread类及其对应的接口runnable上 Thread封装了一个执行线程 为创建一个新线程 程序可以扩展Thread或实现Runnable接口

Thread类常用方法

| 方法                                 | 意义                               |
| ------------------------------------ | ---------------------------------- |
| final String getName()               | 获取线程名                         |
| final int getPriority()              | 获取线程优先级                     |
| final boolean isAlive()              | 确定线程是否运行                   |
| final void join()                    | 等待线程终止                       |
| void run()                           | 线程的进入点                       |
| static void sleep(long milliseconds) | 挂起线程以百万分秒为单位的指定周期 |
| void start()                         | 通过调用线程的run()方法启动线程    |
|                                      |                                    |

所有线程至少有一个主线程的执行线程 从主线程中可以创建其他线程

1. 创建线程

   通过实例化一个Thread对象可以创建一个线程 

   实现Runnable接口方法创建：

   Runnable接口抽象了一个可执行代码单元 通过其定义的run()方法来进行新线程创建 run内定义组成新线程的代码 run()可以调用其他方法 使用其他类 并像主线程那样声明变量 唯一不同的是run()是为程序中的另一个并发执行的线程建立进入点 此线程在run()返回时结束

   创建一个执行Runnable的类后 会在这个类的对象上实例化一个Thread类型的对象 执行Thread的构建函数

   ```java
   Thread(Runnalbe threadOb);//threadOb是实现Runnalbe的实列
   ```

   此函数定义了从哪开始执行线程 创建后使用start()方法开始运行新进程(java16)

   改进MyThreadTest构造中直接实例化Thread对象来完成 并且在创建线程Thread时就为线程命名而不是存储变量名来实例化 再通过getName来获取线程名称

   ```java
   Thread(Runnable threadOb,String name);
   ```

   如果在构造函数内创建了Thread对象后再创建 则再开一个线程但调用的对象属性为同一个对象域

   Thread 扩展进行创建（java17）

   创建多重线程时 java将按自己的方式自由调动线程的执行

2. 判断线程结束 

   ```java
   final boolean isAlive()//调用判断进程是否还在运行 是返回True
   ```

   方法2：等待调用其的线程结束

   ```java
   final void join() throws InterruptedException
   ```

   ```java
   try{ 					//等待线程结束结束时执行do
   	ThreadOb.join();
   }
   catch(InterruptedException{...}
   {do.....}
   ```

3. 线程优先级

   线程的优先级决定了可以被分配到多少的CPU时间

   但同时当一个高优先线程在等待资源时（阻塞）将运行一个较低优先度的线程 高优先度线程得到资源后将占用低优先度线程的CPU时间

   ```java
   final void setPriority(int level);
   //level的值在MIN_PRIORITY 和MAX_PRIORITY之间（目前为1~10）
   //通过设置NORM_PRIORITY（5）设回默认优先度
   ```

4. 同步化

   使用多先时通过同步化协调两个或多个线程的活动（当两线程同时修改一个文件或等待另一个线程的事件发出时）

   通过监视器来实现同步化 监视器通过实现Lock来工作 当一个对象被一个线程锁住时其他线程无法访问该对象 当线程退出解锁对象后其他线程再对对象进行访问（java中的所有对象都拥有一个监视器）
   
   同步化由关键字synchronized 和几个定义完好的方法支持
   
   通过对方法添加synchronized来进行同步化 单个线程同步化时 其他线程无法访问此线程占用的对象 只有等此线程占用对象完成后才能使用（java18）
   
   ```java
   synchronized elemtype Name(elements) {...}
   ```
   
   除了关键字方法进行同步化外还可以通过代码块进行
   
   ```java
   synchronized (object){...}//object是对被同步化的对象的引用
   ```
   
   

# applet



# Swing

Swing GUI 包含两个主要项目 组件和容器 

组件：独立的可视化控件

容器：用于容纳其他组件的特殊组件 三种容器类： JFrame，JDialog JApplet

> 每个GUI在屏幕上显示必须是存在于容器中的，每个GUI组件只能属于一个容器之中 
>
> 可视化组件不是直接放在容器中而是添加到容器的内容面板之中
>
> 可以添加一个菜单栏到容器中 但应位于顶层容器之中并且位于内容面板之外

所有的Swing GUI 都必须至少包含一个容器

组件通常派生与 JComponent类

Swing定义两种容器 第一种位顶级容器 ：Jframe Japplet Jwindow Jdialog（都继承于AWT类 ） 第二种轻量级容器（继承于Jcomponent）

当新建窗口时需要新建一个JFrame型对象 通过此对象进行对窗口容器值的修改 

容器窗体中通常带有菜单栏对象(JMenuBar)和内容面板对象(JPanel)

JFrame： 主要顶层窗口容器

```java
new JFrame()			//新建一个窗口类
```

可以在构造方法中进行标题添加 也可以使用`setTitle("...")`来进行窗口标题的设置

```java
jframe.pack()	//调整窗口大小
```

设置窗口样式

```java
JFrame.setDefaultLookAndFeelDecorated(true)//JFrame的静态方法进行窗口外观可设置选择
jfm.setIconImage(new ImageIcon(imgURL).getImage());//设置窗口图标
```

窗口关闭事件

| DO_NOTHING_ON_CLOSE | 关闭窗口时声明都做不做     |
| ------------------- | -------------------------- |
| HIDE_ON_CLOSE       | 关闭窗口时最小化           |
| DISPOSE_ON_CLOSE    | 关闭窗口时隐藏并释放       |
| EXIT_ON_CLOSE       | 使用System.exit(0)退出程序 |
|                     |                            |

窗口API

| 方法                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| void setDefaultCloseOperation(int)<br />int getDefaultCloseOperation | 设置或获取当前用户按下窗体关闭按钮时的动作                   |
| void setIconImage(Image)<br />Image getIconImage()           | 设置或获取代表窗体的图标参数为一个java.awt.Image对象         |
| void setTitle(String)<br />String getTitle()                 | 设置或获取窗口标题                                           |
| void setUndecorated(boolean)<br />boolean isUndecorated()    | 设置或获取此窗口应该被设置 当窗体未被显示时有效（未被packed或shown时有效） |
| static void setdefaultLookAndFeelDecorated(boolean)          | 决定后续常见的JFrame窗口是否由当前的程序外观所提供的窗口设置 |
| void pack()                                                  | 调整窗口大小                                                 |
| void setSize(int,int)<br />void setSize(Dimension)<br />Dimension getSize() | 设置或获取窗口的全部大小 整数指定对应宽和高                  |
| void setBounds(int,int,int,int)<br />void setBounds(Rectangle)<br />Rectangle getBounds() | 设置或获取窗口的大小和位置 整数参数分别代表左上角x,y坐标位置，宽，高 |
| void setLocation(int,int)<br />Point getLocation()           | 设置或获取窗口左上角(x,y)的位置                              |
| void setLocationRelativeTo(Component)                        | 定位窗口于指定组件的正中位置 如果参数为null则位于屏幕中央 在设置窗口大小后使用此方法 |

根面板相关方法

| 方法                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| void setContentPane(Container)<br />Container getContentPane() | 设置或获取窗体的内容面板                                     |
| JRootPane creatRootPane()<br />void setRootPane(JRootPane)<br />JRootPane getRootPane() | 创建、设置或获取窗体的根面板 根面板管理窗体的内部，包括内容面板，透明面板等 |
| void setJMenuBar(JMenuBar)<br />JMenuBar getJMenuBar()       | 设置或获得窗体菜单来管理一系列窗体的菜单                     |
| void setGlassPane(Component)<br />Component getGlassPane()   | 设置或获取窗体的透明面板 可以使用透明面板来中途截取鼠标事件或在程序的GUI顶部进行绘图 |
| void setLayeredPane(JLayeredPane)<br />JLayeredPane getLayeredPane() | 设置或获取窗体的层面板 可以使用窗体的层面板来将组件放置于其他组件的上面或后面 |





JButton为按钮类 添加时需要添加一个actionPerformed的按钮监听方法 （Java15）同时此分行发是在事件委派线程上进行调用

JTextField为文本输入控件 拥有一个与之关联的动作命令字符串 默认时动作命令字符串为文本域当前内容 可以通过调用setActionCommand()把方法动作命令设置为一个用户选择的值

(java15)

```java
	void setActionCommand(String cmd)
```

(cmd相当于按钮构建时的名字 即通过cmd来确定文本组件的触发)

通过getText()方法来进行文本组件输入的字符串获取

通过setText()方法来设置文本组件中的字符串

JCheckBox 为复选框控件但是继承与JtoggleButton 因此其实复选框是一种特殊的按钮 

```java
JCheckBox(String str)	//创建复选框 str为标签指定
```

当启用护额禁用复选框是将会产生一个项目事件 由ItemEvent类表示 由实现ItemListener接口的类处理 该接口仅指定一个方法

```java
void itemStateChanged(ItemEvent ie)//项目事件在ie中接收
```

要获得对于被修改的项目的引用调用方法

```java
Object getIten()
```

返回的引用必须转化为被处理的组件类

可以通过调用getText()方法获得与复选框关联的文本 通过调用setText()方法来修改此文本

```java
boolean isSelected()	//判断复选框状态 选中返回true否则返回false
```

JList是列表组件 支持一个列表中包含有一个或多个项目 

构造函数：

```java
JList(Object[] items)//JList包含的项目在items数组中
```

大多数时候将JList封装在JScrollPane中 （一个容器可自动将其中的内容进行滚动显示

```java
JScrollPane(Component comp)//comp为需要滚动显示的组件
```

当用户生成或修改选项时JList将会生成一个ListSelectionEvent事件 通过实现ListSelectionListener来实现监听处理 仅有一个方法valueChanged()

```java
void valueChanged(ListSelectionEvent le)
```

le为生成事件对象的引用

默认JList运行用户从列表中选择并修改多个项目 调用setSelectionMode()方法来修改该行为(JList中定义)

```java
void setSelectionMode(int mode)；
    /*mode 值的范围为：
    SINGLE_SELECTION
    SINGLE_INTERVAL_SELECTION
	MULTIPLE_INTERVAL_SELECTION
    */
```

调用getSelectionIndex()方法获取第一个选择的项目的索引 

```java
int getSelectionIndex()//从0开始 当未存在时返回-1
```

```java
int[] getSelectionIndex()//返回所有被选中项目索引的数组
```

JMenuBar为菜单栏组件（可以作为组件的容器）

```java
new JMenuBar()		//新建一个菜单栏对象
Jframe.setJMenuBar(jmb)	//将菜单栏对象添加到容器中
jmb.setPreferredSize(new Dimension(x,y))//设置菜单栏大小
jmb.add(...)			//向菜单栏中添加组件
```

JPanel为内容面板组件（作为组件容器存在）

在JFrame中使用`getContentPane()`来获取顶层容器的内容面板 

使用`setContentPane()`来将一个组件设置为内容面板

```java
new JPanel(new Layout())//创建新内容面板对象(可同时设置流式样式)
jpl.setBorder(...)	//为内容面板设置边框
```

根面板：

每一个顶层容器都依赖于一个隐含的中间容器 “根面板” 其管理着内容面板和菜单栏 其和截取鼠标操作有关

层面版：

在根面板之上 在内容面板和菜单栏之下 

透明面板：
用于截取发生在顶层容器上的输入事件 还可以用于在多个容器上绘制

布局管理器

| 种类          | 描述                                                     |
| ------------- | -------------------------------------------------------- |
| BorderLayout  | 将容器分为东西南北中5个部分每个部分放置一个组件          |
| FlowLayout    | 将容器按行排列当一行排满后换行                           |
| GridLayout    | 将成功布局空间划分为若干行乘若干列的区域组件置于此区域中 |
| GridBagLayout | 前一种的升级版                                           |
| CardLayout    | 将容器中的每一个组件作为一个卡片一次仅一个卡片可见       |
| BoxLayout     | 允许在容器中水平或垂直的方式安排多个组件                 |
| SpringLayout  | 通过定义组件边沿关系来实现布局                           |
| GroupLayout   | 指定一个窗体上组件彼此之间的关系                         |



事件类：

| 事件         | 事件对象                             | 含义                                                         |
| ------------ | ------------------------------------ | ------------------------------------------------------------ |
| 动作事件     | java.awt.event.ActionEvent           | 对应按钮单击、菜单选择、文本框中回车                         |
| 调整事件     | java.awt.event.AdjustmentEvent       | 用户体调整滚动条滑块位置                                     |
| 选项事件     | java.awt.event.ItemEvent             | 复选框的选中状态调整                                         |
| 文本事件     | java.awt.event.TextEvent             | 文本域或文本框中内容发生改变                                 |
| 列表选择事件 | javax.swing.event.ListSelectionEvent | 列表框选项发生变化                                           |
| 组件事件     | java.awt.event.ComponentEvent        | 移动组件、改变组件大小、显示或隐藏组件 此为所有低级事件类的基类 |
| 键盘事件     | java.awt.event.KeyEvent              | 键盘上的一个键被按下或释放                                   |
| 鼠标事件     | java.awt.event.MouseEvent            | 按下、释放鼠标，移动或拖动鼠标                               |
| 焦点事件     | java.awt.event.FocusEvent            | 组件获得或失去焦点                                           |
| 窗口事件     | java.awt.event.WindowEvent           | 窗口被激活、屏蔽、最大化、最小化、关闭                       |

监听器类型：

| 事件监听器名称     | 事件监听器接口                          | 事件处理方法                                                 | 对应的事件         |
| ------------------ | --------------------------------------- | ------------------------------------------------------------ | ------------------ |
| 动作事件监听器     | java.awt.event.ActionListener           | actionPerformed                                              | ActionEvent        |
| 调整事件监听器     | java.awt.event.AdjustmentListener       | adjustmentValueChanged                                       | AdjustmentEvent    |
| 选项事件监听器     | java.awt.event.ItemListener             | itemStateChanged                                             | ItemEvent          |
| 文本事件监听器     | java.awt.event.TextListener             | textValueChanged                                             | TextEvent          |
| 列表选择事件监听器 | javax.swing.event.ListSelevtionListener | valueChanged                                                 | ListSelectionEvent |
| 组件事件监听器     | java.awt.event.ComponentListener        | componentMoved<br />componentHidden<br />componentResized<br />componentShown | ComponentEvent     |
| 键盘事件监听器     | java.awt.event.KeyListener              | keyPressed<br />keyReleased<br />keyTyped                    | KeyEvent           |
| 鼠标事件监听器     | java.awt.event.MouseListener            | mousePressed<br />mouseReleased<br />mouseEntered<br />mouseExited<br />mouseClicked | MouseEvent         |
| 鼠标移动事件监听器 | java.awt.event.MouseMotionListener      | mouseDragged<br />mouseMoved                                 | MouseEvent         |
| 焦点事件监听器     | java.awt.event.FocusListener            | focusGained<br />focusLost                                   | FocusEvent         |
| 窗口事件监听器     | java.awt.event.Window.Listener          | windowClosing<br />windowOpened<br />windowIconified<br />windowDeiconified<br />windowClosed<br />windowActivated<br />windowDeactivated | windowEvent        |

