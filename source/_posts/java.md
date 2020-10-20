---
title: java基础
date: 2018-10-05 09:59:06
tags: java
categories:
---

java 程序设计

<!-- more -->

# java介绍


## java三种核心机制

• Java 虚拟机(Java Virtual Machine)
• 代码安全性检测(Code Security)
• 垃圾收集机制(Garbage collection)

## Java虚拟机（Java Virtual Machine）

>Java 语言里负责解释执行字节码文件的是 Java 虚拟机，即 JVM（Java Virtual Machine）。 JVM 是可运行 Java 字节码文件的虚拟计算机。所有平台上的 JVM 向编译器提供相同的编程接口，而编译器只需要面向虚拟机，生成虚拟机能理解的代码，然后由虚拟机来解释执行。在一些虚拟机的实现中，还会将虚拟机代码转换成特定系统的机器码执行，从而提高执行效率。当使用 Java 编译器编译 Java 程序时，生成的是与平台无关的字节码，这些字节码不面向任何具体平台，只面向 JVM。不同平台上的 JVM 都是不同的，但它们都提供了相同的接口。 JVM 是 Java 程序跨平台的关键部分，只要为不同平台实现了相应的虚拟机，编译后的 Java 字节码就可以在该平台上运行。显然，相同的字节码程序需要在不同的平台上运行，这几乎是“不可能的”，只有通过中间的转换器才可以实现， JVM 就是这个转换器。JVM 是一个抽象的计算机，和实际的计算机一样，它具有指令集并使用不同的存储区域。它负责执行指令，还要管理数据、内存和寄存器 





• 在一台计算机上由软件或硬件模拟的计算机。
• Java虚拟机(JVM)读取并处理经编译过的字节码class文件 。
Java虚拟机规范定义了：
• 指令集
• 寄存器集
• 类文件结构
• 堆栈
• 垃圾收集堆
• 内存区域


## jre

• JRE (The Java Runtime Environment)
• JRE = JVM + API（Lib )
• JRE运行程序时的三项主要功能：
加载代码：由class loader 完成；
校验代码：由bytecode verifier 完成；
执行代码：由 runtime interpreter完成。

## Java自动垃圾回收技术

• 垃圾回收(garbage collection)
• 在C/C++ 等语言中，由程序员负责回收无用内存
• Java语言自动垃圾回收
系统级线程跟踪存储空间的分配情况
在JVM的空闲时，检查并释放那些可被释放的存储器空间
程序员无须也无法精确控制和干预该回收过程





```
通常有如下建议：
  一个 Java 源文件只定义一个类，不同的类使用不同的源文件定义。
  让 Java 源文件的主文件名与该源文件中定义的 public 类同名。

 Java 程序的内存分配和回收都是由
JRE 在后台自动进行的。 JRE 会负责回收那些不再使用的内存，这种机制被称为垃圾回收（Garbage
Collection，也被称为 GC）。通常 JRE 会提供一个后台线程来进行检测和控制，一般都是在 CPU 空闲或
内存不足时自动进行垃圾回收，而程序员无法精确控制垃圾回收的时间和顺序等。
```

>Java 的堆内存是一个运行时数据区，用以保存类的实例（对象）， Java 虚拟机的堆内存中存储着正在运行的应用程序所建立的所有对象，这些对象不需要程序通过代码来显式地释放。一般来说，堆内存的回收由垃圾回收来负责，所有的 JVM 实现都有一个由垃圾回收器管理的堆内存。垃圾回收是一种动态存储管理技术，它自动地释放不再被程序引用的对象，按照特定的垃圾回收算法来实现内存资源的自动回收功能。 

>而在 Java 中，当没有对象引用指向原先分配给某个对象的内存时，该内存便成为垃圾。 JVM 的一个超级线程会自动释放该内存区。垃圾回收意味着程序不再需要的对象是“垃圾信息”，这些信息将被丢弃。 



>通常，垃圾回收具有如下几个特点。
>  垃圾回收机制的工作目标是回收无用对象的内存空间，这些内存空间都是 JVM 堆内存里的内存空间，垃圾回收只能回收内存资源，对其他物理资源，如数据库连接、磁盘 I/O 等资源则无能为力。
>  为了更快地让垃圾回收机制回收那些不再使用的对象，可以将该对象的引用变量设置为 null，
>通过这种方式暗示垃圾回收机制可以回收该对象。
>  垃圾回收发生的不可预知性。由于不同 JVM 采用了不同的垃圾回收机制和不同的垃圾回收算
>法，因此它有可能是定时发生的，有可能是当 CPU 空闲时发生的，也有可能和原始的垃圾回收
>一样，等到内存消耗出现极限时发生，这和垃圾回收实现机制的选择及具体的设置都有关系。
>虽然程序员可以通过调用对象的 finalize()方法或 System.gc()等方法来建议系统进行垃圾回收，
>但这种调用仅仅是建议，依然不能精确控制垃圾回收机制的执行。
>  垃圾回收的精确性主要包括两个方面：一是垃圾回收机制能够精确地标记活着的对象；二是垃
>圾回收器能够精确地定位对象之间的引用关系。前者是完全回收所有废弃对象的前提，否则就
>可能造成内存泄漏；而后者则是实现归并和复制等算法的必要条件，通过这种引用关系，可以
>保证所有对象都能被可靠地回收，所有对象都能被重新分配，从而有效地减少内存碎片的产生。
>  现在的 JVM 有多种不同的垃圾回收实现，每种回收机制因其算法差异可能表现各异，有的当垃
>圾回收开始时就停止应用程序的运行，有的当垃圾回收运行时允许应用程序的线程运行，还有
>的在同一时间允许垃圾回收多线程运行。 





## JDK（Java开发工具包）

>Sun 把 Java 分为 Java SE、 Java EE 和 Java ME 三个部分，而且为 Java SE 和 Java EE 分别提供了 JDK
>和 Java EE SDK（Software Development Kit）两个开发包，如果读者只需要学习 Java SE 的编程知识，则
>可以下载标准的 JDK；如果读者学完 Java SE 之后，还需要继续学习 Java EE 相关内容，也可以选择下载
>Java EE SDK，有一个 Java EE SDK 版本里已经包含了最新版的 JDK，安装 Java EE SDK 就包含了 JDK。 





JDK=JRE+Tools
JRE=JVM+API


• JDK提供的工具
java编译器 javac.exe
java执行器 java.exe
文档生成器 javadoc.exe
java打包器 jar.exe
java调试器 jdb.exe


• JDK安装后的文件夹
Bin 该目录存放工具文件
Jre 该目录存放与java 运行环境相关的文件
• 注：该 Jre与从http://java.com 下载的JRE略有区别
Demo 该目录存放一些示例文件
Include 该目录存放与C相关的头文件
Lib 该目录存放程序库
Db 数据库相关

>2002 年 2 月， Sun 发布了 JDK 历史上最为成熟的版本： JDK 1.4。此时由于 Compaq、 Fujitsu、 SAS、Symbian、 IBM 等公司的参与，使 JDK 1.4 成为发展最快的一个 JDK 版本。到 JDK 1.4 为止，我们已经可以使用 Java 实现大多数的应用了。
>在此期间， Java 语言在企业应用领域大放异彩，涌现出大量基于 Java 语言的开源框架： Struts、
>WebWork、 Hibernate、 Spring 等；大量企业应用服务器也开始涌现： WebLogic、 WebSphere、 JBoss 等，这些都标志着 Java 语言进入了飞速发展时期。 

>JDK 1.5 增加了诸如泛型、增强的 for 语句、可变数量的形
>参、注释（Annotations)、自动拆箱和装箱等功能；同时，也发布了新的企业级平台规范，如通过注释等新特性来简化 EJB 的复杂性，并推出了 EJB 3.0 规范。还推出了自己的 MVC 框架规范： JSF， JSF 规范类似于 ASP.NET 的服务器端控件，通过它可以快速地构建复杂的 JSP 界面。 

>但在 2009 年 4 月 20 日， Oracle 宣布将以每股 9.5 美元的价格收购 Sun，该交易的总价值约为 74亿美元。而 Oracle 通过收购 Sun 公司获得了两项软件资产： Java 和 Solaris。 







## 设定path和classpath Java程序设计

• 设定path和classpath
前者是命令（javac及java)的路径; 后者是所要引用的类的路径
可以在命令行上设定
• set path=.;c:\jdk\bin;…
也可以在系统环境中设定
• 如win7中：我的电脑—属性—高级—性能—环境变量
• 如win8中：这台电脑—属性—高级—环境变量
• 在javac及java命令行上使用-classpath （或-cp)选项可以引用别的库
javac –cp libxx.jar 源文件名.java
java –cp libxx.jar 类名



## 设置环境变量



> 'java' 不是内部或外部命令，也不是可运行的程序
> 或批处理文件。
> 'javac' 不是内部或外部命令，也不是可运行的程序
> 或批处理文件。



> 这意味着我们还不能使用 java 和 javac 两个命令。这是因为： 虽然我们已经在计算机里安装了 JDK，而 JDK 的安装路径下也包含了 java 和 javac 两个命令，但计算机不知道到哪里去找这两个命令。计算机如何查找命令呢？ Windows 操作系统根据 Path 环境变量来查找命令。 Path 环境变量的值是一系列路径， Windows 操作系统将在这一系列的路径中依次查找命令，如果能找到这个命令，则该命令 是可执行的；否则将出现“'xxx'不是内部或外部命令，也不是可运行的程序或批处理文件”的提示。而 Linux 操作系统则根据 PATH 环境变量来查找命令， PATH 环境变量的值也是一系列路径。 因为 Windows 操作系统不区分大小写，设置 Path 和 PATH 并没有区别；而 Linux 系统是区分大小写的，设置 Path 和PATH 是有区别的，因此只需要设置 PATH 环境变量即可。 



>那么 CLASSPATH 环境变量的作用是什么呢？当使用“java Java 类名”命令来运行 Java 程序时，
>JRE 到哪里去搜索 Java 类呢？可能有读者会回答，在当前路径下搜索啊。这个回答很聪明，但 1.4 以前
>版本的 JDK 都没有设计这个功能，这意味着即使当前路径已经包含了 HelloWorld.class，并在当前路径
>下执行“java HelloWorld”，系统将一样提示找不到 HelloWorld 类。
>如果使用 1.4 以前版本的 JDK，则需要在 CLASSPATH 环境变量中添加一点（.），用以告诉 JRE 需要在当前路径下搜索 Java 类。除此之外，编译和运行 Java 程序还需要 JDK 的 lib 路径下 dt.jar 和 tools.jar 文件中的 Java 类，因此还需要把这两个文件添加到 CLASSPATH 环境变量里。因此，如果使用 1.4 以前版本的 JDK 来编译和运行 Java 程序，常常需要设置 CLASSPATH 环境变量的值为.;%JAVA_HOME%\lib\dt.jar; %JAVA_HOME%\lib\tools.jar（其中 JAVA_HOME 环境变量应指向JDK 的安装目录）。 



```
如果想在运行 Java 程序时临时指定 JRE 搜索 Java 类的路径，则可以使用-classpath 选项，即按如下
格式来运行 java 命令：
java -classpath dir1;dir2;dir3...;dirN Java 类
-classpath 选项的值可以是一系列的路径，多个路径之间在 Windows 平台上以分号（;）隔开，在
Linux 平台上则以冒号（:）隔开。
如果在运行 Java 程序时指定了-classpath 选项的值， JRE 将严格按-classpath 选项所指定的路径来搜
索 Java 类，既不会在当前路径下搜索 Java 类， CLASSPATH 环境变量所指定的搜索路径也不再有效。
```





----------------------------------



> JAVA_HOME：该环境变量的值就是 Java 所在的目录，一些 Java 版的软件
> 和一些 Java 的工具需要用到该变量，设置 PATH 和 CLASSPATH 的时候，
> 也可以使用该变量以方便设置。

> PATH：指定一个路径列表，用于搜索可执行文件的。
> 执行一个可执行文件时，如果该文件不能在当前路径下找到，
> 则依次寻找 PATH 中的每一个路径，直至找到。或者找完 PATH 中的路径也不能找到，则报错。
> Java 的编译命令 (javac)，执行命令 (java) 和一些工具命令 (javadoc, jdb 等) 都在其安装路径下的 bin 目录中。
> 因此我们应该将该路径添加到 PATH 变量中。

> CLASSPATH：也指定一个路径列表，是用于搜索 Java 编译或者运行时需要用到的类。
> 在 CLASSPATH 列表中除了可以包含路径外，还可以包含 .jar 文件。
> Java 查找类时会把这个 .jar 文件当作一个目录来进行查找。
> 通常，我们需要把 JDK 安装路径下的 jre\lib\rt.jar (Linux: jre/lib/rt.jar) 包含在 CLASSPATH 中。

`PATH 和 CLASSPATH 都指定路径列表，列表中的各项 (即各个路径) 之间使用分隔符分隔。
在 Windows 下，分隔符是分号 (;)，而在 Linux 下，分隔符是冒号 (:)。`



### windows xp下配置JDK环境变量：

 安装JDK，安装过程中可以自定义安装目录等信息，
 例如我们选择安装目录为C:\Program Files\Java\jdk1.6.0_10；

在“系统变量”中，设置3项属性，JAVA_HOME,PATH,CLASSPATH(大小写无所谓),
若已存在则点击“编辑”，不存在则点击“新建”；


JAVA_HOME指明JDK安装路径，就是刚才安装时所选择的路径C:\Program Files\Java\jdk1.6.0_10，
此路径下包括lib，bin，jre等文件夹（此变量最好设置，因为以后运行tomcat，eclipse等都需要依据此变量）；

Path使得系统可以在任何路径下识别java命令，设为： 

%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin; 


CLASSPATH为java加载类(class or lib)路径，只有类在classpath中，java命令才能识别，设为： 

.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar (要加.表示当前路径) 



# 面向对象

## 对象（object)
• 对象具有两方面的含义：
在现实世界中：
• 是客观世界中的一个实体
在计算机世界中：
• 是一个可标识的存储区域




## 类（class）

• 类：具有共同属性和行为的对象集合
属性： 变量（字段 field)
行为： 函数（方法 method）
• 类与对象的关系
类是对象的抽象(模板)
对象是类的实例

• 注：类和对象有时都统称“对象”，为了明确起见，后者称为“对象实例”


## 面向对象的三大特征
封装性
继承性
多态性

### 封装 （Encapsulation） 



> 封装指的是将对象的实现细节隐藏起来，然后通过一些公用方法来暴露该对象的功能 

模块化：将属性和行为封装在类中，程序定义很多类。
信息隐蔽：将类的细节部分隐藏起来
用户只通过受保护的接口访问某个类。

class Person{
private int age;
public int getAge(){ return age; }
public void setAge(int a){ age=a;}
String name;
void sayHello(){…}
}

### 继承（inheritance)



>继承是面向对象实现软件复用的重要手段，当子类继承父类后，子类作为一种特殊的父类，将直接获得父类的属性 和方法 .
>
>由于多继承可能引起继承结构的混乱，而且会大大降低程序的可理解性，所以 Java
>不支持多继承。 

• 继承性
父类和子类之间共享数据和方法
• 继承的好处
更好地进行抽象与分类
增强代码的重用率
提高可维护性

### 多态性（polymorphism)



>多态指的是子类对象可以直接赋给父类变量，但运行时依然表现出子类的行为特征，这意味着
>同一个类型的对象在执行同一个方法时，可能表现出多种行为特征。 

• 多态
不同的对象收到同一个消息（调用方法）可产生完全不同的效果
实现的细节则由接收对象自行决定
例 foo( Person p ){ p.sayHello(); }
 foo( new Student() );
 foo( new Teacher() );





**在编程语言领域，还有一个“基于对象”的概念，这两个概念极易混淆。通常而言，“基于对象”
也使用了对象，但是无法利用现有的对象模板产生新的对象类型，继而产生新的对象，也就是说，“基于对象”没有继承的特点；而“多态”则更需要继承，没有了继承的概念也就无从谈论“多态”。面向对象方法的三大基本特征（封装、继承、多态）缺一不可。例如， JavaScript 语言就是基于对象的，它使用一些封装好的对象，调用对象的方法，设置对象的属性；但是它们无法让开发者派生新的类，开发者只能使用现有对象的方法和属性。 **


## java的面向对象

> 在 Java 语言中，除了 8 个基本数据类型值之外，一切都是对象，而对象就是面向对象程序设计的中心。 Java 通过为对象定义 Field（以前常被称为属性，现在也称为字段）来描述对象的状态 
> 对象是 Java 程序的核心，所以 Java 里的对象具有唯一性，每个对象都有一个标识来引用它，如果某个对象失去了标识，这个对象将变成垃圾，只能等着系统垃圾回收机制来回收它。 Java 语言不允许直接访问对象，而是通过对对象的引用来操作对象。

一般→特殊关系：这种关系就是典型的继承关系， Java 语言使用 extends 关键字来表示这种继承
关系， Java 的子类是一种特殊的父类。因此，这种一般→特殊的关系其实是一种“is a”关系.
比如水果→苹果，就是典型的一般→特殊的关系，苹果 is a 水果


## 三种基本结构



1. 顺序
2. 条件
3. 循环



>结构化程序设计中的任何结构都具有唯一的入口和唯一的出口，
>并且程序不会出现死循环。在程序的静态形式与动态执行流程之间具有良好的对应关系。 





## 如何设计

>从面向对象的眼光来看，开发者希望从自然的认识、使用角度来定义和使用类。也就是说，开发者
>希望直接对客观世界进行模拟：定义一个类，对应客观世界的哪种事物；业务需要关心这个事物的哪些
>状态，程序就为这些状态定义 Field；业务需要关心这个事物的哪些行为，程序就为这些行为定义方法 



• 认为客观世界由各种对象组成
• 程序的分析和设计都围绕着
有哪些对象类
每个类有哪些属性、哪些方法
类之间的关系（继承、关联等）
对象之间发送消息（调用方法）



## Java程序的类型

Application和Applet程序

• 结构和运行环境不同
• 前者是独立的程序，需要执行器(调用虚拟机)来运行
• 后者是嵌在HTML网页中的非独立的程序，
由专门的appletViewer来运行
或者由Web 浏览器（调用JAVA虚拟机）来运行



## 其他几个工具 Java程序设计
• 主要的工具
javac 编译
java 运行（控制台及图形界面程序）
javaw 运行图形界面程序
appletViewer 运行applet程序
• 另外常用的几个工具
jar 打包工具
javadoc 生成文档
Javap 查看类信息及反汇编


## Java的API文档

• 在线文档
http://docs.oracle.com/javase/8/docs/api/index.html
• 也可以下载网页格式的文档
doc.zip
• 另可以从网上搜索到chm格式的文档
如 JDK_API_1_6_zh_CN.CHM

# 简单程序构造



## 文档注释



> 一种功能更强大的注释形式：文档注释。如果编写 Java 源代码时添加了合适的文
> 档注释，然后通过 JDK 提供的 javadoc 工具可以直接将源代码里的文档注释提取成一份系统的 API 文档。 



**什么是API**:开发一个大型软件时， 需要定义成千上万的类，而且需要很多人参与开发。每个人都会开发一些类，并在类里定义一些方法、 Field 提供给其他人使用，但其他人怎么知道如何使用这些类和方法呢？这时候就需要提供一份说明文档， 用于说明每个类、 每个方法的用途。 当其他人使用一个类或一个方法时， 他无须关心这个类或这个方法的具体实现，他只要知道这个类或这个方法的功能即可，然后使用这个类或方法来实现具体的目的，也就是通过调用应用程序接口（API）来编程。 API 文档就是用以说明这些应用程序接口的文档。对于 Java 语言而言， API 文档通常详细说明了每个类、每个方法的功能及用法等。

java英文api：https://docs.oracle.com/javase/8/docs/api/
java中文api：http://www.matools.com/api/java8


### 使用javadoc

>javadoc 工具默认只处理以 public 或 protected 修饰的类、接口、方法、 Field、构造器和内部类之前的文档注释。如果开发者确实希望 javadoc 工具可以提取 private 修饰的内容，则可以在使用 javadoc 工具时增加-private 选项。
>文档注释以斜线后紧跟两个星号（/**）开始，以星号后紧跟一个斜线（*/）作为结尾，中间部分
全部都是文档注释，会被提取到 API 文档中。

## 编译与解释



### 编译

>编译型语言是指使用专门的编译器，针对特定平台（操作系统）将某种高级语言源代码一次性“翻
>译”成可被该平台硬件执行的机器码（包括机器指令和操作数），并包装成该平台所能识别的可执行性
>程序的格式，这个转换过程称为编译（Compile）。编译生成的可执行性程序可以脱离开发环境，在特定
>的平台上独立运行。
>有些程序编译结束后，还可能需要对其他编译好的目标代码进行链接，即组装两个以上的目标代码
>模块生成最终的可执行性程序，通过这种方式实现低层次的代码复用。
>因为编译型语言是一次性地编译成机器码，所以可以脱离开发环境独立运行，而且通常运行效率较
>高；但因为编译型语言的程序被编译成特定平台上的机器码，因此编译生成的可执行性程序通常无法移
>植到其他平台上运行；如果需要移植，则必须将源代码复制到特定平台上，针对特定平台进行修改，至
>少也需要采用特定平台上的编译器重新编译。
>现有的 C、 C++、 FORTRAN、 Pascal 等高级语言都属于编译型语言。 

### 解释



>解释型语言是指使用专门的解释器对源程序逐行解释成特定平台的机器码并立即执行的语言。解释
>型语言通常不会进行整体性的编译和链接处理，解释型语言相当于把编译型语言中的编译和解释过程混
>合到一起同时完成。
>可以认为：每次执行解释型语言的程序都需要进行一次编译，因此解释型语言的程序运行效率通常
>较低，而且不能脱离解释器独立运行。但解释型语言有一个优势：跨平台比较容易，只需提供特定平台
>的解释器即可，每个特定平台上的解释器负责将源程序解释成特定平台的机器指令即可。解释型语言可
>以方便地实现源程序级的移植，但这是以牺牲程序执行效率为代价的。
>现有的 Ruby、 Python 等语言都属于解释型语言。 

### java

>由 Java 语言编写的程序需要经过编译步骤，但这个编译步骤并不会生成特定
>平台的机器码，而是生成一种与平台无关的字节码（也就是*.class 文件）。当然，这种字节码不是可执
>行性的，必须使用 Java 解释器来解释执行。 

```
Java 解释器规定：如需某个类能被解释器直接解释执行，则这个类里必须包含 main 方法，而且 main
方法必须使用 public static void 来修饰，且 main 方法的形参必须是字符串数组类型（String[] args 是字
符串数组的形式）。也就是说， main 方法的写法几乎是固定的。 Java 解释器就从这个 main 方法开始解
释执行，因此， main 方法是 Java 程序的入口。
```





## java程序的基本构成



### 命名

>Java 程序源文件的命名不是随意的， Java 文件的命名必须满足如下规则。
> Java 程序源文件的后缀必须是.java，不能是其他文件后缀名。
> 在通常情况下， Java 程序源文件的主文件名可以是任意的。但有一种情况例外：如果 Java 程序
>源代码里定义了一个 public 类，则该源文件的主文件名必须与该 public 类（也就是该类定义使
>用了 public 关键字修饰）的类名相同。
>由于 Java 程序源文件的文件名必须与 public 类的类名相同，因此，一个 Java 源文件里最多只能定
>义一个 public 类。 



```
通常有如下建议：
  一个 Java 源文件只定义一个类，不同的类使用不同的源文件定义。
  让 Java 源文件的主文件名与该源文件中定义的 public 类同名。
```





• 应注意Java是大小写敏感的语言。
按Java惯例，类名首字母用大写（Pascal)
其余的（包名、方法名、变量名）首字母都小写(camel)
少用下划线
变量、常量随使用随定义 



• 类＝类头＋类体
• 类成员＝字段（field）＋方法（method）
字段（field, 属性,变量） 方法（method, 函数）
• 方法＝方法头＋方法体



### 分隔符

Java 语言里的分号（;）、花括号（{}）、方括号([])、圆括号（()）、空格、圆点（.）都具有特殊的分
隔作用，因此被统称为分隔符。 



>花括号的作用就是定义一个代码块，一个代码块指的就是“{”和“}”所包含的一段代码，代码块
在逻辑上是一个整体。对 Java 语言而言，类定义部分必须放在一个代码块里，方法体部分也必须放在一个代码块里。除此之外，条件语句中的条件执行体和循环语句中的循环体通常也放在代码块里。花括号一般是成对出现的，有一个“{”则必然有一个“}”，反之亦然。


### 关键字

**Java 的所有关键字都是小写的**

>除了上面的 48 个关键字之外， Java 还包含 goto 和 const 两个保留字（reserved word），保留字的意思是， Java 现在还未使用这两个单词作为关键字，但可能在未来的 Java 版本中使用这两个单词作为关键字；不仅如此， Java 还提供了 3 个特殊的直接量（literal）： true、 false 和 null； Java 语言的标识符也不能使用这两个保留字和三个特殊的直接量。


## 程序的编辑、编译与运行
• 源程序编辑
可用任一文本编辑器
• 程序编译
使用JDK中的javac工具
• 程序运行
使用java工具


## Application的编辑、编译与运行

• 程序编辑：编辑器——文件名要与public class的类名一致
区分大小写
• 程序编译——转换为字节码（bytecode)文件，扩展名.class
（.class文件中包含 java虚拟机的指令）
编译可以使用JDK工具javac.exe。
如 javac Hello.java
• 程序的运行——执行 .class文件中的指令的过程。
如 java Hello
(注意：不要写成 java Hello.class， 因为这里需要的是类名，不是文件名)


## Applet的编辑、编译与运行

• Java Applet程序必须嵌入到 HTML中，并由负责解释HTML 文件的
WWW 浏览器充当解释器，解释执行程序。
• Java Applet在WWW 中引入了动态交互的内容。
• 1、源程序的编辑和编译。
• 2、在HTML文件中嵌入Applet。
使用`<applet>`标签:
<applet code="HelloWorldApplet.class"
width=200 height=40 background=white>

用appletViewer运行Applet
• appletViewer HelloWorldApplet.html

## 使用jar打包
• （1）编译 javac A.java
• （2）打包 jar cvfm A.jar A.man A.class
c表示创建(create), v表示显示详情(verbose), f表示指定文件名, m表示清单文件
• （3）运行 java -jar A.jar
• 其中A.man 是清单文件(manifest), 内容如下：
• Manifest-Version: 1.0
• Class-Path: .
• Main-Class: A
• 清单文件可以任意命名，常见的是用 MANIFEST.MF

## 使用JavaDoc生成文档

```
javadoc 命令可对源文件、包生成 API 文档，在上面的语法格式中， Java 源文件可以支持通配符，
例如，使用*.java 来代表当前路径下所有的 Java 源文件。 javadoc 的常用选项有如下几个。
  -d <directory>：该选项指定一个路径，用于将生成的 API 文档放到指定目录下。
  -windowtitle <text>：该选项指定一个字符串，用于设置 API 文档的浏览器窗口标题。
  -doctitle <html-code>：该选项指定一个 HTML 格式的文本，用于指定概述页面的标题。
只有对处于多个包下的源文件来生成 API 文档时，才有概述页面。
  -header <html-code>：该选项指定一个 HTML 格式的文本，包含每个页面的页眉。
除此之外， javadoc 命令还包含了大量其他选项，读者可以通过在命令行窗口执行 javadoc -help 来
查看 javadoc 命令的所有选项
```





• javadoc –d 目录名 xxx.java
• `/** */` 这其中可以用以下标记
@author 对类的说明 标明开发该类模块的作者
@version 对类的说明 标明该类模块的版本
@see 对类、属性、方法的说明 参考转向，也就是相关主题
@param 对方法的说明 对方法中某参数的说明
@return 对方法的说明 对方法返回值的说明
@exception 对方法的说明 对方法可能抛出的异常进行说明

## 使用javap

• 使用javap查看类的信息
javap 类名
• 使用javap反汇编
javap –c 类名


## IDE中快速输入代码
• 代码模板（Code Template)

• 在Eclipse中
输入main，再按Alt+/键，得到main函数
输入sysout，再按Alt+/键，即可得到System.out.println("");
更多的，可见 Window—Preferences—Java—Editor—Templates


• 在NetBeans中
输入psvm，再按Tab键， 得到main函数
输入sout，再按Tab键，即可得到System.out.println("");
更多的，可见 工具—选项—编辑器—代码模板

## 输入与输出 Java程序设计
• 应用程序（Java Application）的输入输出可以是文本界面，也可以是图形界面。
• 小程序（Java Applet）则只能是图形界面。
• 每种界面都可以有输入和输出。





# 数据类型和运算符



基本类型（Primitive Type）和引用类型（Reference Type） 

数据类型决定数据的存储方式和运算方式.
Java中的数据类型分为两大类
基本数据类型（primitive types）
引用类型( reference types )

有的时候也把 char 型称为字符型，实际上字符型也是一种整数类型。 







## 强类型

>Java 语言是一门强类型语言。 强类型包含两方面的含义： ① 所有的变量必须先声明、 后使用； ② 指
>定类型的变量只能接受类型与之匹配的值。 

>基本类型大致上可以分为两类：数值类型和布尔类型，其中数值类型包括整型、字符型和浮点型，所有数值类型之间可以进行类型转换，这种类型转换包括自动类型转换和强制类型转换。 





## 四类/八种基本数据类型



### boolean

boolean类型数据只允许取值true或false 



### char

字符常量是用单引号括起来的单个字符.
Java字符采用Unicode编码，每个字符占两个字节，
可用十六进制编码形式表示
char c1 = '\u0061';

#### 转义字符

```
• \ddd 1到3位八进制数所表示的字符(ddd)
• \uxxxx 1到4位十六进制数所表示的字符(xxxx)
• \' 单引号字符
• \" 双引号字符
• \\ 反斜杠字符
• \r 回车
• \n 换行
• \f 走纸换页
• \t 横向跳格
• \b 退格
```

### 整数类型

byte 1字节 
short 2字节 
int 4字节 
long 8字节 

• Java语言整型常量的三种表示形式：
 十进制整数，如12, -314, 0。
 八进制整数，要求以0开头，如012
 十六进制数，要求0x或0X开头，如0x12
 二进制数，以0b或0B开头，如0b00010010 （Java7以上）

• Java语言的整型常量默认为int型，如：
• int i =3;
• 声明long型常量可以后加‘ l ’或‘ L ’ ，如：
• long l = 3L;
• Java中没有“无符号数”
** 可以用long来处理无符号整数（uint）**


### 浮点

| 类 型  | 占用存储空间 | 表数范围             |
| ------ | ------------ | -------------------- |
| float  | 4字节        | -3.403E38~3.403E38   |
| double | 8字节        | -1.798E308~1.798E308 |

• Java浮点型常量默认为double型,
如要声明一个常量为float型，则需在数字后面加f或F，如：
• double d = 3.14;
• float f = 3.14f;





## 关系运算符



比较运算的结果是一个布尔值（true 或 false）。 Java支持的比较运算符如下。 

• 关系运算符: >，<，>=，<=，==，!= 

### 优先级

> 关系运算符优先级大于赋值运算符，小于算术运算符。
>
> ==与!=的优先级是关系运算符里较低的。
>
> boolean类型不能比大小。





浮点数的运算是有误差的。所以比较两个浮点数**是否相等**，不能直接相比较，而是判断俩个数相减是否小于一个很小的数。

```
double a =1.1+1.1;
double b=2.2；
`Math.abs(a=b)  小于 1 e -8` ;


```







## 输入输出

使用java.util.Scanner类

• java.io包
• System.in.read( )
• System.out.print( ) 及 println、 printf （类似于C语言）


### 读输入

```
Scanner in = new Scanner(System.in);
System.out.println(in.nextLine());



• System.out.println(in.nextLine());

```









## 位运算符

```


• 左移
"a<<b; "将二进制形式的a逐位左移b位，最低位空出的b位补0；
• 带符号右移
"a>>b; "将二进制形式的a逐位右移b位，最高位空出的b位补原来的符号位；
• 无符号右移
"a>>>b;"将二进制形式的a逐位右移b位，最高位空出的b位补0。


• 移位运算符性质
适用数据类型:byte、 short、 char、 int、 long
对低于int型的操作数将先自动转换为int型再移位（整型提升，对所有的运算
都是这样）
对于int型整数移位a>>b，系统先将b对32取模，得到的结果才是真正移位的
位数
对于long型整数移位时a>>b ，则是先将移位位数b对64取模




```



| 2227 =      | 00000000 00000000 00001000 10110011 |
| ----------- | ----------------------------------- |
| 2227<< 3 =   | 00000000 00000000 01000101 10011000 |
| 2227>>3 =   | 00000000 00000000 00000001 00010110 |
| 2227>>>3 =  | 00000000 00000000 00000001 00010110 |
| -2227 =     | 11111111 11111111 11110111 01001101 |
| -2227<<3 =  | 11111111 11111111 10111010 01101000 |
| -2227>>3 =  | 11111111 11111111 11111110 11101001 |
| -2227>>>3 = | 00011111 11111111 11111110 11101001 |





## 扩展赋值运算符

| 运算符 | 用法举例 | 等效的表达式 |
| ------ | -------- | ------------ |
| +=     | a += b   | a = a+b      |
| -=     | a -= b   | a = a-b      |
| *=     | a *= b   | a = a*b      |
| /=     | a /= b   | a = a/b      |
| %=     | a %= b   | a = a%b      |
| `&`=     | a `&`= b   | a = a`&b `     |
| \|=    | a \|= b  | a = a\|b     |
| ^=     | a ^= b   | a = a^b      |
| <<=    | a <<= b  | a = a<<b     |
| >>=    | a >>= b  | a = a>>b     |
| >>>=   | a >>>= b | a = a>>>b    |





## 字符串连接运算符



"+"运算符两侧的操作数中只要有一个是字符串(String)类型，系统会自动将另一
个操作数转换为字符串然后再进行连接
• int i = 300 +5;
• String s = "hello, " + i + "号";
• System.out.println(s); //输出：hello, 305号
• 该运算符大大简化了字符串的处理 

## 逻辑运算符

逻辑运算符用于操作两个布尔型的变量或常量。逻辑运算符主要有如下 6 个。
  &&：与，前后两个操作数必须都是 true 才返回 true，否则返回 false。
  &：不短路与，作用与&&相同，但不会短路。
  ||：或，只要两个操作数中有一个是 true，就可以返回 true，否则返回 false。
  |：不短路或，作用与||相同，但不会短路。
  !：非，只需要一个操作数，如果操作数为 true，则返回 false；如果操作数为 false，则返回 true。
  ^：异或，当两个操作数不同时才返回 true，如果两个操作数相同则返回 false。 

## 三目运算符

```
(expression) ? if-true-statement : if-false-statement;
先对逻辑表达式 expression 求值，如果逻辑表达式返回 true，则返回第二个
操作数的值，如果逻辑表达式返回 false，则返回第三个操作数的值
```











## 运算优先级



| Separator | . ( ) { } ; , |
| --------- | ------------- |
|           |               |

| Associative | Operators                               |
| ----------- | --------------------------------------- |
| R to L      | ++ -- ~ ! (data type)                   |
| L to R      | * / %                                   |
| L to R      | + -                                     |
| L to R      | << >> >>>                               |
| L to R      | < > <= >= instanceof                    |
| L to R      | == !=                                   |
| L to R      | &                                       |
| L to R      | ^                                       |
| L to R      | \|                                      |
| L to R      | &&                                      |
| L to R      | \|\|                                    |
| R to L      | ?:                                      |
| R to L      | = *= /= %= += -= <<= >>= >>>= &= ^= \|= |

# 条件



> 级联：
>
```
if()
...;
else if()
....;
else if()
...;
else
...;

```



if 语句使用布尔表达式或布尔值作为分支条件来进行分支控制。 if 语句有如下三种形式。
第一种形式：
if ( logic expression )
{
statement...
}
第二种形式：
if (logic expression)
{
statement...
}
else
{
statement...
}
第三种形式：
if (logic expression)
{
statement...
}
else if(logic expression)
{
statement...
}
...//可以有零个或多个 else if 语句
else//最后的 else 语句也可以省略
{
statement...
} 



## 多路分支里 switch



break; 很重要，请注意。

>• 使用switch要注意：
>变量类型是整数、字符、字符串（String)
>case后面是常量
>注意 break 



```
switch (expression)
{
case condition1:
{
statement(s)
break;
}
case condition2:
{
statement(s)
break;
}
...
case conditionN:
{
statement(s)
break;
}
default:
{
statement(s)
}
}
```



# 循环



>循环的五个要素
>初始化部分（init_statement）
>循环条件部分（test_exp）
>循环体部分（body_statement）
>迭代部分（alter_statement）
>结束后处理 

## 三种循环

```

for:

语法格式
• for (init_statement; test_exp; alter_statement)｛
• body_statement
• ｝
• 应用举例
• int result = 0;
• for(int i=1; i<=100; i++) {
• result += i;
• }
• System.out.println("result=" + result);

while:

语法格式 [init_statement]
• while( test_exp)｛
• body_statement;
• [alter_statement;]
• }
• 应用举例 int result = 0;
• int i=1;
• while(i<=100) {
• result += i;
• i++;
• }
• System.out.println("result=" + result);
• 注意不要死循环

do-while:

语法格式
• [init_statement]
• do｛
• body_statement;
• [alter_statement;]
• ｝while( test_exp);
• 应用举例
• int result = 0, int i=1;
• do{
• result += i;
• i++;
• }while(i<=100);
• System.out.println("result=" + result);


```





## 特俗流程控制语句



```
break 语句
 break语句用于终止某个语句块的执行
 { ……
 break;
 ……
 }
 break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块
 label1: { ……
 label2: { ……
 label3: { ……
 break label2;
 ……
 }
 }
 }

 continue 语句
 continue语句用于跳过某个循环语句块的一次执行
 continue语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环
```



## 使用return结束循环






>return 关键字并不是专门用于结束循环的， return 的功能是结束一个方法。当一个方法执行到一个
return 语句时（return 关键字后还可以跟变量、常量和表达式，这将在方法介绍中有更详细的解释），这个方法将被结束
return 直接结束整个方法，不管这个 return 处于多少层循环之内。 



## code



```
	
	死循环：
	public static void main(String[] args) {
		//循环的初始化条件、循环条件、循环迭代语句都在下面一行
		for (int count = 0 ; count < 10 ; count++)
		{
		System.out.println(count);
		//再次修改了循环变量
		count *= 0.1; //死循环？？？ 因为count是整型
		}
		System.out.println("循环结束!");
```



### 数位数



> 给你一个整数，算出几位数。。





```

1.

//		初始化
		Scanner in=new Scanner(System.in);
		
		Long number=in.nextLong();
		int count=0;
		
		while(number>0)
		{
			number/=10;
			count++;
		}
		


		System.out.println("共有 "+(count)+" 位数");
```



### 算平均数



> 输入很多正数，以-1结束。
>
>

```

1.

package project;

//求平均值

import java.util.Scanner;

public class SumNumber {
	
	public static void main(String[] args) {
		
		Scanner in =new Scanner(System.in);
		int sum=0;
		int count=0;
		int number=in.nextInt();
		
		
		while(number != -1)
		{
			sum+=number;
			count++;
			number=in.nextInt();
			
		}
		if(count>0)
		{
			System.out.println("the avrage is "+(double)sum/count);
		}
	}

}


```



### 猜数

```
package project;

//给一个1到100以内的整数，猜出它来

import java.util.Scanner;

public class SuspectNumber {
	public static void main(String[] args) {
		Scanner in=new Scanner(System.in);
		double number=(int)(Math.random()*100+1);//[0,1)-->[0,100)-->[1,101)
		
		int a;
		int count=0;
		
		do {
			a=in.nextInt();
			count++;
			if(a>number)
			{
				System.out.println("偏大");
			}else if(a<number)
				System.out.println("偏小");
		}while(a!=number);
		System.out.println("ok, 你猜中了");
		
		
		
		System.out.println("恭喜你，你猜了 "+count+"次");
		
		
	}

}

```





### 整数分解


> 352%10--->2
352/10%10--->5
352/10/10%10--->3
3/10=0用来做判断

```java
package project;

import java.util.Scanner;
public class IntegerDisaway {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int number;
		int result=0;
		
		number=in.nextInt();
		
		do {
			
			int digit=number%10;
			result=result*10+digit;//解决首位是0的问题
			System.out.print(digit); //900--->009
			number /=10;
		}while(number!=0);
		System.out.println();
		System.out.println(result);
	}

}

```





### 阶乘

a=++i;

a=i++;

```
package project;

//不能算很大的阶乘！！

import java.util.Scanner;

public class Factorial {
	public static void main(String[] args) {
		Scanner in =new Scanner(System.in);
		int n=in.nextInt();
//		int i=1;
		
		int factorial=1;
		
//		while(i<=n){
//			factorial*=i;
//			i++;
//		}
		
		for(int i=1;i<=n;i++)
		{
			factorial*=i;
		}
//		System.out.println(i);
		System.out.println(factorial);
	}

}

```

### 素数





```
package project;

//判断一个数是不是素数

import java.util.Scanner;

public class Prime {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int n = in.nextInt();
		
		int flag=0;
		
		for(int i=2;i<n;i++)
		{
			if(n%i==0)
			{
				flag=1;
				break;
			}
		}
		if(flag==0)
		{
			System.out.println("素数 "+n);
		}else
			System.out.println(n+" not prime");
		
	}

}



100以内的素数：

package project;

//判断一个数是不是素数

import java.util.Scanner;

public class Prime {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int n = in.nextInt();
		
//		int flag=0;
		
		
		for(int j=2;j<n;j++)
		{
			int flag=0;
			for(int i=2;i<j;i++)
			{
				if(j%i==0)
				{
					flag=1;
					break;
				}
			}
			if(flag==0)
			{
//				System.out.println("素数：");
				System.out.print(j+" ");
			}
//			else
//				System.out.println(n+" not prime");
		}	
	}

}


前50个素数：


```



### 凑硬币

> 1角，2角，5角凑10元



```
package project;

//凑钱找零 1,2,5角

import java.util.Scanner;

public class Balance {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int amount=in.nextInt();
		
		lable1:for(int one=0 ;one<amount*10;one++)
		{
			lable2:for(int two=0;two<amount*5;two++)
			{
				lable3:for(int five=0;five<amount*2;five++)
				{
					if(one+two*2+five*5==amount*10)
					{
						System.out.println(one+"个一角  "+two+"个2角   "+five+" 个5角 ");
						break lable1;
					}
				}
			}
		}
	}
}

```



### 求分数和

```

1.  
1+1/2+1/3+1/4+1/5..1/n


package project;

//就和1+1/2+1/3+1/4+1/5..1/n

import java.util.Scanner;

public class SumFraction {
	public static void main(String[] args) {
		Scanner in =new Scanner(System.in);
		int n=in.nextInt();
		double result=0.0;
		
		for(int i=1;i<=n;i++)
		{
			result+=1.0/i;
		}
		System.out.println(result);
		System.out.printf("%.2f",result);
	}

}


2. 
1-1/2+1/3-1/4+1/5..1/n  一加一减


package project;

//就和1+1/2+1/3+1/4+1/5..1/n
// 1-1/2+1/3-1/4+1/5..1/n

import java.util.Scanner;

public class SumFraction {
	public static void main(String[] args) {
		Scanner in =new Scanner(System.in);
		int n=in.nextInt();
		double result=0.0;
		
//		for(int i=1;i<=n;i++)
//		{
//			result+=1.0/i;
//		}
		
//		int sign=1;
//		
//		for(int i=1;i<=n;i++)
//		{
//			
//			result+=sign*1.0/i;
//			sign=-sign;
//		}
		
		for(int i=1;i<=n;i++)
		{
			if(i%2==1)  //奇位为正
			{
				result+=1.0/i;
			}
			else//偶为负
			{
				result-=1.0/i;
			}
			
		}
		
		
		
		
		System.out.println(result);
		System.out.printf("%.2f",result);
	}

}



```



### 求最大公约数

```
枚举：

package project;

//求两个数的最大公约数

import java.util.Scanner;

public class GCD {
	public static void main(String[] args) {
		Scanner in=new Scanner(System.in);
		
		int gcd =1;
		int a=in.nextInt();
		int b=in.nextInt();
		
		for(int i=1;i<=a&&i<=b;i++)
		{
			if(a%i==0 && b%i==0)
			{
				gcd=i;
			}
		}
		
		System.out.println("最大公约数是 "+gcd);
		
	}

}

辗转相除法：

package project;

//求两个数的最大公约数

import java.util.Scanner;

public class GCD {
	public static void main(String[] args) {
		Scanner in=new Scanner(System.in);
		
		int gcd =1;
		int a=in.nextInt();
		int b=in.nextInt();
		
//		for(int i=1;i<=a&&i<=b;i++)
//		{
//			if(a%i==0 && b%i==0)
//			{
//				gcd=i;
//			}
//		}
		
		while(b!=0)
		{
//			辗转相除法
			
			int temp=a%b;
			a=b;
			b=temp;
			
		}
		gcd=a;
		
		System.out.println("最大公约数是 "+gcd);
		
	}

}


```





# 数组



## 概述

>Java 语言支持两种语法格式来定义数组：
>type[] arrayName;
>type arrayName[];
>对这两种语法格式而言，通常推荐使用第一种格式。因为第一种格式不仅具有更好的语意，而且具
>有更好的可读性。对于 type[] arrayName;方式， 很容易理解这是定义一个变量， 其中变量名是 arrayName，
>而变量类型是 type[]。前面已经指出： type[]确实是一种新类型，与 type 类型完全不同（例如 int 类型是
>基本类型，但 int[]是引用类型）。因此，这种方式既容易理解，也符合定义变量的语法。但第二种格式
>type arrayName[]的可读性就差了， 看起来好像定义了一个类型为 type 的变量， 而变量名是 arrayName[]，
>这与真实的含义相去甚远。
>可能有些读者非常喜欢 type arrayName[];这种定义数组的方式，这可能是因为早期某些计算机读物
>的误导，从现在开始就不要再使用这种糟糕的方式了 

>• 数组是多个相同类型数据的组合
>• 一维数组的声明方式：
>• int[] a;
>• double []b
>• Mydate []c;
>• 注意方括号写到变量名的前面，也可以写到后面 

## 数组初始化 	
• 数组定义 与 为数组元素分配空间 分开进行 



>数组是一种引用类型的变量，因此使用它定义一个变量时，仅仅表示定义了一个引用变量（也就是
>定义了一个指针），这个引用变量还未指向任何有效的内存，因此定义数组时不能指定数组的长度。而
>且由于定义数组只是定义了一个引用变量，并未指向任何有效的内存空间，所以还没有内存空间来存储
>数组元素，因此这个数组也不能使用，只有对数组进行初始化后才可以使用。 




### 静态初始化

```
在定义数组的同时就为数组元素分配空间并赋值。

int[] a = { 3, 9, 8};
或写为 int[] a = new int[]{ 3, 9, 8 };
MyDate[] dates= {
new MyDate(22, 7, 1964),
new MyDate(1, 1, 2000),
new MyDate(22, 12, 1964)
};
注：最后可以多一个逗号。如{3,9,8,}
```



### 默认初始化/动态初始化



```
• 数组是引用类型，
• 数组一经分配空间，其中的每个元素也被按照成员变量同样的方式被
隐式初始化。例如：
( 数值类型是0， 引用类型是null )
• int []a= new int[5];
• //a[3]则是0


执行动态初始化时，程序员只需指定数组的长度，即为每个数组元素指定所需的内存空间，系统将
负责为这些数组元素分配初始值。指定初始值时，系统按如下规则分配初始值。
  数组元素的类型是基本类型中的整数类型（byte、 short、 int 和 long），则数组元素的值是 0。
  数组元素的类型是基本类型中的浮点类型（float、 double），则数组元素的值是 0.0。
  数组元素的类型是基本类型中的字符类型（char），则数组元素的值是'\u0000'。
  数组元素的类型是基本类型中的布尔类型（boolean），则数组元素的值是 false。
  数组元素的类型是引用类型（类、接口和数组），则数组元素的值是 null。
```



>不要同时使用静态初始化和动态初始化，也就是说，不要在进行数组初始化时，既指
>定数组的长度，也为每个数组元素分配初始值。 



## 一维数组

>• Java语言中声明数组时不能指定其长度(数组中元素的个数)，例如：
>• int a[5]; //非法
>• 数组是引用类型
> int [ ] a = new int[5];
> 这里 a 只是一个引用 

```
• 每个数组都有一个属性length指明它的长度，例如：a.length 指明数组a的
长度(元素个数)；
int[] ages = new int[10];
for ( int i=0; i<ages.length; i++ )
{
System.out.println( ages[i] );
}
```





## 增强的for



> 从 Java 5 之后， Java 提供了一种更简单的循环： foreach 循环，这种循环遍历数组和集合 .使用 foreach 循环遍历数组和集合元素时，无须获得数组和集合长度，无须根据索引来访问数组元素和集合元素， foreach 循环自动遍历数组和集合的每个元素。 



>Enhanced for语句可以方便地处理数组、集合中各元素
>• 如：
>int[] ages = new int[10];
>for ( int age ： ages )
>{
>System.out.println( age );
>}
>这种语句是只读式的遍历 

>**当使用 foreach 来迭代访问数组元素时， foreach 中的循环变量相当于一个临时**
>**变量，系统会把数组元素依次赋给这个临时变量，而这个临时变量并不是数组元素，它只是保存了数组**
>**元素的值。因此，如果希望改变数组元素的值，则不能使用这种 foreach 循环。** 





## 复制数组



> System.arraycopy方法提供了数组元素复制功能：
>//源数组
>int[] source = { 1, 2, 3, 4, 5, 6 };
>// 目的数组
>int []dest = { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 };
>// 复制源数组中从下标0开始的source.length个元素到
>// 目的数组， 从下标0的位置开始存储。
>System.arraycopy( source, 0, dest, 0, source.Length ); 


## 二维数组

```
int[][] a =new int[3][5];
//3行5列








> 二维数组举例：
> `int [][] a `=
> `{{1,2},{3,4,0,9},{5,6,7}}; `



> 二维数组是数组的数组
> `int [][] t = new int [3][];`
> t[0] = new int[2];
> t[1] = new int[4];
> t[2] = new int[3]; 



> 多维数组的声明和初始化应按从高维到低维的顺序进行
> `int t1[][] = new int [][4]; //非法, 这与C++不同 `
```





## code
## 深入数组


>数组引用变量只是一个引用，这个引用变量可以指向任何有效的内存，只有当该引用指向有效内存
>后，才可通过该数组变量来访问数组元素。

>实际的数组对象被存储在堆（heap）内存中； 如果引用该数组对象的数组引用变量是一个局部变量，那么它被存储在栈（stack）内存中。


### 堆与栈

>当一个方法执行时， 每个方法都会建立自己的内存栈， 在这个方法内定义的变量将会逐个放入这块栈内存里，随着方法的执行结束，这个方法的内存栈也将自然销毁。因此，所有在方法中定义的局部变量都是放在栈内存中的；当我们在程序中创建一个对象时，这个对象将被保存到运行时数据区中，以便反复利用（因为对象的创建成本通常较大），这个运行时数据区就是堆内存。 堆内存中的对象不会随方法的结束而销毁，即使方法结束后，这个对象还可能被另一个引用变量所引用（在方法的参数传递时很常见），则这个对象依然不会被销毁。 只有当一个对象没有任何引用变量引用它时， 系统的垃圾回收器才会在合适的时候回收它。


>如果堆内存中数组不再有任何引用变量指向自己，则这个数组将成为垃圾，该数组所占的内存将会
>被系统的垃圾回收机制回收。因此，为了让垃圾回收机制回收一个数组所占的内存空间，可以将该数组变量赋为 null，也就切断了数组引用变量和实际数组之间的引用关系，实际的数组也就成了垃圾。

>>**必须牢记：定义并初始化一个数组后，在内存中分配了两个空间，一个用于存放数组的引用变量(一般在栈里）；**
>>**另一个用存放数组本身（在堆里）这部分是在堆内存里运行的，通常无法直接访问它，只能通过数组引用变量来访问，失去引用的数组，就变成了垃圾。**

### 基本类型数组；引用类型数组



**引用类型数组：每个数组元素里存储的还是引用，它指
向另一块内存，这块内存里存储了有效数据 



```
public class ReferenceArrayTest
{
public static void main(String[] args)
	{
		//定义一个 students 数组变量，其类型是 Person[]
		Person[] students;
		//执行动态初始化
		students = new Person[2];
		//创建一个 Person 实例，并将这个 Person 实例赋给 zhang 变量
		Person zhang = new Person();
		//为 zhang 所引用的 Person 对象的 age、 height 赋值
		zhang.age = 15;
		zhang.height = 158;
		//创建一个 Person 实例，并将这个 Person 实例赋给 lee 变量
		Person lee = new Person();
		//为 lee 所引用的 Person 对象的 age、 height 赋值
		lee.age = 16;
		lee.height = 161;
		//将 zhang 变量的值赋给第一个数组元素
		students[0] = zhang;
		//将 lee 变量的值赋给第二个数组元素
		students[1] = lee;
		//下面两行代码的结果完全一样，因为 lee
		//和 students[1]指向的是同一个 Person 实例
		lee.info();
		students[1].info();
	}
}
```

>执行 Person[] students;代码时，这行代码仅仅在栈内存中定义了一个引用变量，也就是一个指针，这个指针并未指向任何有效的内存区。
>直到执行初始化，本程序对 students 数组执行动态初始化，动态初始化由系统为数组元素分配默认的初始值： null，即每个数组元素的值都是 null,
> 接着的代码定义了 zhang 和 lee 两个 Person 实例，定义这两个实例实际上分配了 4 块内存，在栈内存中存储了 zhang 和 lee 两个引用变量，还在堆内存中存储了两个 Person 实例。
> 此时 students 数组的两个数组元素依然是 null，直到程序依次将 zhang 赋给 students 数组的第一个元素，把 lee 赋给 students 数组的第二个元素， students 数组的两个数组元素将会指向有效的内存区。


### 投票统计



> 0~9,统计各出现多少次

### 素数

> 1.偶数不是素数；去掉偶数后，从3到x-1,每次加2
>
> 2.. 无需到x-1，只要到sqrt(x)遍；

**前50**个素数：

```

int cnt=1;
primes[0]=2;
LOOP1:
		for(int x=3;cnt<50;x++)//取数从3开始，小于cnt个;x
		{
			for(int i=0;i<cnt;i++)//判断是不是素数 i为数组下标
			{
				if(x%primes[i]==0)
				{
					continue LOOP1;
				}
					
			}
			primes[cnt++]=x;
		}
```



**构造素数表**：100以内

1. 素数的倍数都不是素数

```
boolean[] isPrime= new boolean[100];
		for(int i=0;i<isPrime.length;i++)//设为全是素数
		{
			isPrime[i]=true;
		}
		
		for(int i=2;i<isPrime.length;i++)//i*k倍
		{
			if(isPrime[i])
			{
				for(int k=2;i*k<isPrime.length ;k++)
				{
					isPrime[i*k]=false;
				}
			}
		}
		
		
		for(int i=2;i<isPrime.length;i++)
		{
			if(isPrime[i]==true)
			{
				System.out.print(i+" ");
			}
		}
```





# 使用对象



## 字符串



>字符串变量和数组变量类似，它并不存放字符串，不是字符串的所有者，它是字符串的管理者。

> Java的字符串还是一种特殊的“不可变”对象，所有的字符串操作都是产生一个新的字符串，而不是对原来的字符串的修改。对这一点的理解颇为重要。

String s=new String("hhhhh");

String s = "oooo";



## StringBuffer

由于String 的+ 操作比较大。



所以：

```
StringBuffer sb=new StringBuffer();
sb.append();
...
sb.toString();//产生了String对象


```







>字符也是Java中基础的数据类型之一，Java采用Unicode16表达字符，在所有的机器上，不管CPU、操作系统和本地语言，字符类型是一致和统一的。
>一个字符的常量是用单引号包围起来的一个字符，如'a'、'*'、'好'。一个汉字也是Unicode的一个字符，所以也是Java的一个字符。

>回车：到行的首字符 \r
>换行：换到新行 \n


## 包裹类型



对于基本数据类型，Java提供了对应的包裹(wrap)类型。这些包裹类型将一个基本数据类型的数据转换成对象的形式，从而使得它们可以像对象一样参与运算和传递。下表列出了基本数据类型所对应的包裹类型：

| 基本类型 | 包裹类型  |
| -------- | --------- |
| boolean  | Boolean   |
| char     | Character |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |

我们看到，除了int和char以外，包裹类型就是把基本类型的名字的第一个字母大写。在Java的系统类库中，所有第一个字母大写的，都是类的名字。所以在编辑程序的时候，一定要小心大小写，以免一不小心犯错。



## code

字符：
```
package oh;

public class Char {
	public static void main(String[] args) {
		char a='a';
		System.out.println(a+1);//字符加数字，结果是数字
		System.out.println('A'+1);
		
		char b;
		b=(char)(a+111);
		
		System.out.println(b);
		
		System.out.println('a'>'b');
		
		
	}

}

```





**类，字段，方法**

>•类是组成Java程序的基本要素
>• 是一类对象的原型
>• 它封装了一类对象的状态和方法
>它将变量与函数封装到一个类中

>• 字段（field）是类的属性，是用变量来表示的。
>字段又称为域、域变量、属性、成员变量等
>• 方法（method）是类的功能和操作, 是用函数来表示的


>• 构造方法（constructor )是一种特殊的方法
>• 用来初始化（new)该类的一个新的对象
>• 构造方法和类名同名，而且不写返回数据类型。
>• Person( String n, int a ){
>• name = n;
>• age = a;
>• }

>• 一般情况下，类都有一个至多个构造方法
>• 如果没有定义任何构造方法，系统会自动产生一个构造方法，称为默
>认构造方法（default constructor）。
>• 默认构造方法不带参数，并且方法体为空。

>• 方法重载（overloading)：多个方法有相同的名字，编译时能识别出
>来。
>• 这些方法的签名（signature)不同，或者是参数个数不同，或者是参
>数类型不同。
>• 通过方法重载可以实现多态（polymorphism） 。



## this

1．在方法及构造方法中，使用this来访问字段及方法


2．使用this解决局部变量与域同名的问题
• 使用this还可以解决局部变量（方法中的变量）或参数变量与域变
量同名的问题。如，在构造方法中，经常这样用：
• Person( int age, String name ) {
• this.age = age;
• this.name = name;
• }
• 这里，this.age表示域变量，而age表示的是参数变量。

3．构造方法中，用this调用另一构造方法
• 构造方法中，还可以用this来调用另一构造方法。如：
• Person( )
• {
• this( 0, "" );
• ……
• }
• 在构造方法中调用另一构造方法，则这条调用语句必须放在第一句。



>this 关键字总是指向调用该方法的对象。根据 this 出现位置的不同，
>this 作为对象的默认引用有两种情形：
>¾ 构造器中引用该构造器正在初始化的对象；
>¾ 在方法中引用调用该方法的对象。
>this 关键字最大的作用就是让类中一个方法， 访问该类里的另一个方法或 Field。 

# 函数





Java的函数必须定义在类的内部，成为类的成员。定义一个函数，要像这样写：

```
<返回类型> <方法名称>(<参数表>) {

	<方法体>

}
```

> 返回类型是这个函数运行结束时要返回给调用者的数据的类型，函数可以返回基本数据类型、对象或者void。返回void表示这个函数不返回任何值。函数名称是一个Java名字，一样要遵循和变量一样的命名规则。参数表是0个或1个或多个参数定义，用逗号’,’分隔。

> 在这个阶段，我们要在所有的函数的返回类型前面加上关键字“static”。static表示这个函数属于这个类，而不属于这个类的任何对象，因此我们才可以不制造这个类的对象，而直接从main()函数中调用它。

> 当一个函数被调用时，程序就转到这个函数中去运行，函数体里的语句就一条一条地被调用。一旦函数运行结束，就又回到调用它的地方去继续运行。





> **  形参与实参，参数与值 **
> java 永远都是值传递！！！
> 那么当数组或是对象呢？？？


>本地变量默认不会初始化。
>而函数的参数在进入函数的时候初始化了。





**方法位置**：

在面向对象编程语言里，类才是一等公民，整个系统由一个个的类组成。因此在 Java 语言里，方法不能独立存在，方法必须属于类或对象。 

>因此，如果需要定义方法，则只能在类体内定义，不能独立定义一个方法。一旦将一个方法定义在
某个类的类体内，如果这个方法使用了 static 修饰，则这个方法属于这个类，否则这个方法属于这个类
的实例 



>方法不能独立定义，方法只能在类体里定义。
>从逻辑意义上来看，方法要么属于该类本身，要么属于该类的一个对象。 
>永远不能独立执行方法，执行方法必须使用类或对象作为调用者

**值传递**: Java 方法的参数传递机制来控制的， Java 里方法的参数传递方式只有一种：值传递。所谓值传递，就是将实际参数值的副本（复制品）传入方法内，而参数本身不会受到任何影响。

## 形参数量可变：

>从 JDK 1.5 之后， Java 允许定义形参个数可变的参数，从而允许为方法指定数量不确定的形参。如果在定义方法时，在最后一个形参的类型后增加三点（...），则表明该形参可以接受多个参数值，多个参数值被当成数组传入。下面程序定义了一个形参个数可变的方法。

## 方法的重载

>
方法重载的要求就是两同一不同：同一个类中方法名相同，参数列表不同。**至于方法的其他部分，
如方法返回值类型、修饰符等，与方法重载没有任何关系**。


## 成员变量和局部变量

**成员**：当系统加载类或创建该类的实例时，系统自动为成员变量分配内存空间，并在分配内存空间后，自动为成员变量指定初始值。

**局部**：局部变量定义后，必须经过显式初始化后才能使用，系统不会为局部变量执行初始化。这意味着定义局部变量后，系统并未为这个变量分配内存空间，直到等到程序为这个变量赋初始值时，系统才会为局部变量分配内存，并将初始值保存到这块内存中。





# 容器（集合）

linked链表，双向的

>容器是现代程序设计非常基础而重要的手段。

>所谓容器，就是“放东西的东西”。数组可以看作是一种容器，但是数组的元素个数一旦确定就无法改变，这在实际使用中是很大的不足。一般意义上的容器，是指具有自动增长容量能力的存放数据的一种数据结构。在面向对象语言中，这种数据结构本身表达为一个对象。所以才有“放东西的东西”的说法。

>Java具有丰富的容器，Java的容器具有丰富的功能和良好的性能。熟悉并能充分有效地利用好容器，是现代程序设计的基本能力。

>顺序容器，即放进容器中的对象是按照指定的顺序（放的顺序）排列起来的，而且允许具有相同值的多个对象存在。

*在一些书中，将容器（英文为collection或container）翻译为“集合”，由于数学中的集合（Set）也是一种特定的容器类型，我们认为将collection翻译为集合是不恰当的。所以我们只会使用容器一词。*

**Iterator** :

**迭代器 Iterator (所有的Collection都能产生）**
Iterator iterator = iterable.iterator();//得到迭代器
while( iterator.hasNext()) doSomething( iterator.next());//遍历 ，iterator.next()得到里面的东西

* iterator.hasNext()//返回Boolean，是否有东西
* iterator.next()//得到东西

## 对象 for-each循环：

### 要个可迭代对象(enhanced for)或叫for-each 

因为是管理者，管理者管理的东西都是同一个的话，就可以改变堆里的值了。



```
用for-each：
//for( Element e : list ) doSomething(e);
  for (Photo photo : album){
  System.out.println( photo.toString() );
 }
 
 编译器生成了Iterator的while(hasNext（)) {….next() }
```



## Collection 接口

![](/images/javaweb/a6.png)

> Collectiion,接口，有两个子接口：
>
> * List: (Collection的子接口)记录元素的保存顺序，且允许有重复元素 
> * Set: (Collection的子接口) 不记录元素的保存顺序，且不允许有重复元素 

**api:**

+add(element : Object) : boolean
+remove(element : Object) : boolean
+size() : int
+isEmpty() : boolean
+contains(element : Object) : boolean
+iterator() : Iterator



### List 接口 线性表（linear list）

> 主要的实现类是 **<u>ArrayList. LinkedList</u>**， 以及早期的Vector 

```
public interface List<E> extends Collection<E> {
 E get(int index);
 E set(int index, E element);
 void add(int index, E element);
 E remove(int index);
 int indexOf(Object o);
....
 }
```

## 顺序容器 ArrayList

泛型；

定义的时候，得给出两个类型：容器的类型，元素的类型



```
import java.util.ArrayList;

ArrayList<String> notes=new ArrayList<String>();

这个<>读作of 用来存放String的

方法：

notes.add();
notes.size();





```

### ArrayList 操作

索引也是从零开始的。下标也会越界。

方法：
add(index,string);// 把原先的东西往后推，腾出来放
get(index);//得到index 位置的内容

remove(int)// 删除内容，返回所删除的内容，删了之后，下标往前推

.toArray(a) //把内容给a

## 集合容器 set

> 两个重要实现：
>
> * HashSet，靠哈希码实现
> * TreeSet，靠TreeMap实现，树实现

> 集合就是数学中的集合的概念：所有的元素都具有唯一的值，元素在其中没有顺序。
>
> 也就是，
>
> * hashCode()不等
> * 如果hashCode相等，再看equals 或者 == 是否为false
>
> > **什么叫无序？**;无法保证元素的添加顺序，但还是按照一定的算法来排的
> >
> > LinkedHashset : 保证元素添加的自然顺序
> >
> > TreeSet : 保证元素的自然顺序
> >
> > HashSet底层维护的table数组添加的顺序是由加入的字符串中的具体字符以及字符串的长度决定的
> >
> >
> >
> >
>
>

```
HashSet

HashSet<String> hs=new HashSet<String>();
hs.add(s);
hs.contains(s);//retrun boolean
for-each可以用


```



## Map 映射

> 两个实现HashMap,TreeMap
>
> 键只能一个。

* **键-值对（key-value pair）的集合** 

其中可以取到

* entrySet()项 的集合
* keySet()键的集合
* values()值的集合


 Map.Entry是一个嵌套接口 Map里定义的接口



![](/images/javaweb/a7.png)

``` java

Map<String,String> map=new HashMap<>();
```



### 散列表 HashMap



> 传统意义上的Hash表，是能以int做值，将数据存放起来的数据结构。Java的Hash表可以以任何实现了hash()函数的类的对象做值来存放对象。

> Hash表是非常有用的数据结构，熟悉它，充分使用它，往往能起到事半功倍的效果。

> **美元里**
> 硬币1分 peny
> 5分	nickel
> 10分  dime
> 25分	quarter



```java
HashMap<k,value>

private HashMap<Integer,String> coinnames=new HashMap<Integer,String>();//Integer,String  都是对象

方法：
coinnames.put(,);//放入东西
coinnames.get();//没有的话就是null 由键得值，参数是key

coinnames.containsKey(int);//boolean 存在这个键吗

coinnames.keySet().size()//coinnames.keySet()得到一个HashMap对象,size()得到元素个数

code:
coinnames.put(1,"rrr");

======================

System.out.println(coinnames.keySet());
System.out.println(coinnames);
结果：
[1, 50, 5, 25, 10]
{1=penny, 50=五毛, 5=nickel, 25=quarter, 10=dime}
》》由toString()方法来实现



```



### 遍历HashMap

```
for(Integer k:coinnames.keySet())
{
    String s=coinnames.get(k);
    System.out.println(s);
}

```



### HashTable

> 实现了Map,及Dictionary接口。

## Stack与Queue

### Stack,栈继承自Vector属于LIst

java.util.Stack;

> 是遵循“后进先出” (Last In First Out, LIFO)原则 .

**三个方法**：

public Object push(Object item)：将指定对象压入栈中。
public Object pop()：将 栈最上面的元素从栈中取出，并返回这个对象。
public boolean empty()：判断栈中没有对象元素。 

```

import java.util.Stack;

Stack<String> stk=new Stack<>();
```



### Queue，队列，接口，实现类LinkedList

>import java.util.LinkedList;
>import java.util.Queue;

队列遵循**“先进先出”** (First In First Out，FIFO)的原则
固定在**一端输入数据(称为入队)，另一端输出数据(称为出队)**。 



函数：

| 功能            | 可抛出异常的 | 返回元素的，没有的话返回null |
| --------------- | ------------ | ---------------------------- |
| Insert（插入）  | add(e)       | offer(e)                     |
| Remove（移除）  | remove()     | poll()                       |
| Examine（检查） | element()    | peek()                       |



```
Queue<String> que=new LinkedList<>();
```








## 对象数组：

>**当数组的元素的类型是类的时候，<u>数组</u>的每一个元素其实只是对象的管理者而不是对象本身。因此，仅仅创建数组并没有创建其中的每一个对象！**


```
String[] a=new String[10];
a[0].length()会出错。
里面存放的都是null.
```







## 直接输出容器



```
ArrayList<String> a=new ArrayList<String>();
HashSet<String> b=new HashSet<String>();

a.add("hi");
a.add("hi");
a.add("hey");

b.add("hi");
b.add("hi");
b.add("hey");

System.out.println(a);//放在了System.out.println()里面了。
System.out.println(b);


结果：
[hi, hi, hey]
[hi, hey]
```





## 早期集合对比

• Vector， 现多用 ArrayList
**相当于动态数组**(比JDK1.0中的 ArrayList好), elementAt,
• Stack， 现多用 LinkedList
Stack是Vector的子类, push, pop, peek
• Hashtable， 现多用 HashMap
Hashtable实现Map接口, 参见Properties类
• Enumeration， 现多用Iterator
Enumeration用另一种方式实现Iterator的功能
如Vector可以得到枚举器
`Enumeration<E> e = v.elements();`
while(e.hasMoreElements()) doSomething(e.nextElement()) 


# 封装Encapsulation 



>它指的是将对象的状态信息隐藏在对象内部，不允许外部程序直接访问对象内部信息，而是通过该类所提供的方法来实现对内部信息的操作和访问。

封装是面向对象编程语言对客观世界的模拟，客观世界里的 Field 都是被隐藏在对象内部的，外界
无法直接操作和修改。就如刚刚说的 Person 对象的 age Field，只能随着岁月的流逝， age Field 才会增加，通常不能随意修改 Person 对象的 age Field。对一个类或对象实现良好的封装，可以实现以下目的。
* 隐藏类的实现细节。
* 让使用者只能通过事先预定的方法来访问数据，从而可以在该方法里加入控制逻辑，限制对 Field
的不合理访问。
* 可进行数据检查，从而有利于保证对象信息的完整性。
* 便于修改，提高代码的可维护性。

为了实现良好的封装，需要从两个方面考虑。
* 将对象的 Field 和实现细节隐藏起来，不允许外部直接访问。
* 把方法暴露出来，让方法来控制对这些 Field 进行安全的访问和操作。
因此，封装实际上有两个方面的含义：把该隐藏的隐藏起来，把该暴露的暴露出来。这两个方面都
需要通过使用 Java 提供的访问控制符来实现




## 使用访问控制符




>private（当前类访问权限）：如果类里的一个成员（包括 Field、方法和构造器等）使用 private
访问控制符来修饰，则这个成员只能在当前类的内部被访问。很显然，这个访问控制符用于修
饰 Field 最合适，使用它来修饰 Field 就可以把 Field 隐藏在该类的内部。


>default（包访问权限）：如果类里的一个成员（包括 Field、方法和构造器等）或者一个外部类不
使用任何访问控制符修饰，我们就称它是包访问权限， default 访问控制的成员或外部类可以被
相同包下的其他类访问。


>protected（子类访问权限）：如果一个成员（包括 Field、方法和构造器等）使用 protected 访问
控制符修饰，那么这个成员既可以被同一个包中的其他类访问，也可以被不同包中的子类访问。
在通常情况下，如果使用 protected 来修饰一个方法，通常是希望其子类来重写这个方法。


>public（公共访问权限）：这是一个最宽松的访问控制级别，如果一个成员（包括 Field、方法和
构造器等）或者一个外部类使用 public 访问控制符修饰，那么这个成员或外部类就可以被所有
类访问，不管访问类和被访问类是否处于同一个包中，是否具有父子继承关系。



**建议**：

类里的绝大部分 Field 都应该使用 private 修饰，只有一些 static 修饰的、类似全局变量的 Field，
才可能考虑使用 public 修饰。除此之外，有些方法只是用于辅助实现该类的其他方法，这些方
法被称为工具方法，工具方法也应该使用 private 修饰。

如果某个类主要用做其他类的父类，该类里包含的大部分方法可能仅希望被其子类重写，而不
想被外界直接调用，则应该使用 protected 修饰这些方法。

希望暴露出来给其他类自由调用的方法应该使用 public 修饰。 因此， 类的构造器通过使用 public
修饰，从而允许在其他地方创建该类的实例。因为外部类通常都希望被其他类自由使用，所以
大部分外部类都使用 public 修饰。

## 类的访问修饰符public

对于**外部类**而言，它也可以使用访问控制符修饰，但外部类只能有两种访问控制级别：` public 和默认`，外部类不能使用 private 和 protected 修饰，<u>因为外部类没有处于任何类的内部，也就没有其所在类的内部、所在类的子类两个范围，因此 private 和 protected 访问控制符对外部类没有意义</u>。外部类可以使用 public 和包访问控制权限，使用 public 修饰的外部类可以被所有类使用，如声明变量、创建实例；不使用任何访问控制符修饰的外部类只能被同一个包中的其他类使用。


## package   与 import

>package 语句必须作为源文件的第一条非注释性语句，一个源文件只能指定一个包，即只能包含一
条 package 语句，该源文件中可以定义多个类，则这些类将全部位于该包下。
如果没有显式指定 package 语句，则处于默认包下。在实际企业开发中，通常不会把类定义在默认
包下

>同一个包下的类可以自由访问，例如下面的 HelloTest 类，如果把它也放在 lee 包下，则这个 HelloTest类可以直接访问 Hello 类，无须添加包前缀。

**import 语句中的星号（*）只能代表类，不能代表包。因此使用 import lee.*;语句时，它表明导
入 lee 包下的所有类**



**导入静态方法**：
静态导入使用 import static 语句，静态导入也有两种语法，分别用于导入指定类的单个静态 Field、
方法和全部静态 Field、方法，其中导入指定类的单个静态 Field、方法的语法格式如下：
`import static package.subpackage...ClassName.fieldName|methodName;`

# 继承

解决代码复制，代码复制是代码质量不良的一种体现

将来要维护时，麻烦，不具有可扩展性

父类有什么，子类就有什么，能不能用呢？？访问权限问题

**继承表达了一种is-a关系，就是说，子类的对象可以被看作是父类的对象。比如鸡是从鸟派生出来的，因此任何一只都可以被称作是一只鸟。但是反过来不行，有些鸟是鸡，但并不是所有的鸟都是鸡。如果你设计的继承关系，导致当你试图把一个子类的对象看作是父类的对象时显然很不合逻辑，比如你让鸡类从水果类得到继承，然后你试图说：这只本鸡是一种水果，所以这本鸡煲就像水果色拉。这显然不合逻辑，如果出现这样的问题，那就说明你的类的关系的设计是不正确的。Java的继承只允许单继承，即一个类只能有一个父类。**


## 子类与父类的关系

>对理解继承来说，最重要的事情是，知道哪些东西被继承了，或者说，子类从父类那里得到了什么。答案是：所有的东西，所有的父类的成员，包括变量和方法，都成为了子类的成员，**除了构造方法。构造方法是父类所独有的，因为它们的名字就是类的名字，所以父类的构造方法在子类中不存在。**除此之外，子类继承得到了父类所有的成员。

>**但是得到不等于可以随便使用**。每个成员有不同的访问属性，子类继承得到了父类所有的成员，但是不同的访问属性使得子类在使用这些成员时有所不同：有些父类的成员直接成为子类的对外的界面，有些则被深深地隐藏起来，即使子类自己也不能直接访问。下表列出了不同访问属性的父类成员在子类中的访问属性：


|父类成员访问属性 |在父类中的含义| 在子类中的含义|
|---|---|---|
|private |只有自己可以访问 |不能访问|
|缺省| 只有包内其它类可以访问 |如果子类与父类在同一个包内：只有包内其它类可以访问 否则：相当于private，不能访问|
|protected |只有包内其它类、自己和子类可以访问 |只有包内其它类、自己和子类可以访问|


public的成员直接成为子类的public的成员，protected的成员也直接成为子类的protected的成员。Java的protected的意思是包内和子类可访问，所以它比缺省的访问属性要宽一些。而对于父类的缺省的未定义访问属性的成员来说，他们是在父类所在的包内可见，如果子类不属于父类的包，那么在子类里面，这些缺省属性的成员和private的成员是一样的：不可见。父类的private的成员在子类里仍然是存在的，只是子类中不能直接访问。我们不可以在子类中重新定义继承得到的成员的访问属性。**如果我们试图重新定义一个在父类中已经存在的成员变量，那么我们是在定义一个与父类的成员变量完全无关的变量，在子类中我们可以访问这个定义在子类中的变量，在父类的方法中访问父类的那个。尽管它们同名但是互不影响。**



>在构造一个子类的对象时，父类的构造方法也是会被调用的，而且父类的构造方法在子类的构造方法之前被调用。在程序运行过程中，子类对象的一部分空间存放的是父类对象。因为子类从父类得到继承，在子类对象初始化过程中可能会使用到父类的成员。**所以父类的空间正是要先被初始化**的，然后子类的空间才得到初始化。在这个过程中，**如果父类的构造方法需要参数，如何传递参数就很重要了。**


### 初始化

定义初始化，构造器

super() 默认是这个。









>类是规则，用来制造对象的规则。我们不断地定义类，用定义的类制造一些对象。类定义了对象的属性和行为，就像图纸决定了房子要盖成什么样子。

>一张图纸可以盖很多房子，它们都是相同的房子，但是坐落在不同的地方，会有不同的人住在里面。假如现在我们想盖一座新房子，和以前盖的房子很相似，但是稍微有点不同。任何一个建筑师都会拿以前盖的房子的图纸来，稍加修改，成为一张新图纸，然后盖这座新房子。所以一旦我们有了一张设计良好的图纸，我们就可以基于这张图纸设计出很多相似但不完全相同的房子的图纸来。

>基于已有的设计创造新的设计，就是面向对象程序设计中的继承。在继承中，新的类不是凭空产生的，而是基于一个已经存在的类而定义出来的。通过继承，新的类自动获得了基础类中所有的成员，包括成员变量和方法，包括各种访问属性的成员，无论是public还是private。当然，在这之后，程序员还可以加入自己的新的成员，包括变量和方法。显然，通过继承来定义新的类，远比从头开始写一个新的类要简单快捷和方便。继承是支持代码重用的重要手段之一。

>类这个词有分类的意思，具有相似特性的东西可以归为一类。比如所有的鸟都有一些共同的特性：有翅膀、下蛋等等。鸟的一个子类，比如鸡，具有鸟的所有的特性，同时又有它自己的特性，比如飞不太高等等；而另外一种鸟类，比如鸵鸟，同样也具有鸟类的全部特性，但是又有它自己的明显不同于鸡的特性。

>如果我们用程序设计的语言来描述这个鸡和鸵鸟的关系问题，首先有一个类叫做“鸟”，它具有一些成员变量和方法，从而阐述了鸟所应该具有的特征和行为。然后一个“鸡”类可以从这个“鸟”类派生出来，它同样也具有“鸟”类所有的成员变量和方法，然后再加上自己特有的成员变量和方法。无论是从“鸟”那里继承来的变量和方法，还是它自己加上的，都是它的变量和方法。




## 继承概述

>• 继承(inheritance)是面向对象的程序设计中最为重要的特征之一
>• 子类（subclass），父类或超类（superclass）
>父类包括所有直接或间接被继承的类

**Java支持单继承：一个类只能有一个直接父类。**

>• Java中的继承是通过extends关键字来实现的
>• class Student extends Person {
>• ……
>• }
>• 如果没有extends子句，则该类默认为java.lang.Object的子类。
>所有的类都是通过直接或间接地继承java.lang.Object得到的。

## 字段

>• 1．字段的继承
> 子类可以继承父类的所有字段
> Student自动具有Person的属性（name，age）

>• 2. 字段的隐藏
> 子类重新定义一个与从父类那里继承来的域变量完全相同的变量，称为域的隐藏。域的隐藏在实际编程中用得
>较少。

>• 3．字段的添加
> 在定义子类时，加上新的域变量，就可以使子类比父类多一些属性。如：
> class Student extends Person
> {
> String school;
> int score;
> }



## 方法

>• 1．方法的继承
>父类的非私有方法也可以被子类自动继承。如，Student自动继承Person的方
>法sayHello和isOlderThan。
>• 2．方法的覆盖(Override)（修改）
>子类也可以重新定义与父类同名的方法，实现对父类方法的覆盖(Override)。







## super

1．使用super访问父类的域和方法
• 注意：正是由于继承，使用this可以访问父类的域和方法。但有时为了明确地指明父类的域和方法，就要用关
键字super。
• 例如：父类Student有一个域age，在子类Student中用age, this.age, super.age来访问age是完全一样的：
• void testThisSuper(){
• int a;
• a = age;
• a = this.age;
• a = super.age;
• }
• 当然，使用super不能访问在子类中添加的域和方法。

• 有时需要使用super以区别同名的域与方法
使用super可以访问被子类所隐藏了的同名变量。
又如，当覆盖父类的同名方法的同时，又要调用父类的方法，就必须使用super。如：
• void sayHello(){
• super.sayHello();
• System.out.println( "My school is " + school );
• }
• 在覆盖父类的方法的同时，又利用已定义好的父类的方法。


2．使用父类的构造方法
• 构造方法是不能继承的
比如，父类Person有一个构造方法Person(String, int)，不能说子类Student也自动有一个构造方
法Student(String, int)。
• 但是，子类在构造方法中，可以用super来调用父类的构造方法。
• Student(String name, int age, String school ){
• super( name, age );
• this.school = school;
• }
• 使用时，super()必须放在第一句。


## 造型

>父类对象与子类对象的转换 Java程序设计
>• 类似于基本数据类型数据之间的强制类型转换，存在继承关系的父类对象和
>子类对象之间也可以在一定条件下相互转换。
>• (1) 子类对象可以被视为其父类的一个对象
>如一个Student对象也是一个Person对象。
>• (2) 父类对象不能被当做其某一个子类的对象。
>• (3) 如果一个方法的形式参数定义的是父类对象，那么调用这个方法时，可
>以使用子类对象作为实际参数。
>• (4) 如果父类对象引用指向的实际是一个子类对象，那么这个父类对象的引
>用可以用强制类型转换（casting)成子类对象的引用

# 多态


## 多态变量


**一个声明类型，动态类型。**



>子类型类似于类的层次,类型也构成了类型层次。子类所定义的类型是其超类的类型的子类型。

当把一个对象赋值给一个变量时,对象的类型必须与变量的类型相匹配,如:

    Car myCar = new Car(); 

是一个有效的赋值,因为Car类型的对象被赋值给声明为保存Car类型对象的变量。但是由于引入 了继承,这里的类型规则就得叙述得更完整些:
​	一个变量可以保存其所声明的类型或该类型的任何子类型。


对象变量可以保存其声明的类型的对象,或该类型的任何子类型的对象。
Java中保存对象类型的变量是多态变量。“多态”这个术语(字面意思是许多形态)是指一个变量可以保存不同类型(即其声明的类型或任何子类型)的对象。



## 向上造型 cast



把子类实例当作父类对象看待！！向上造型，不需要().

>两个类 Vechicle(父类)   Car(子类)

```
造型：

Vechicle v=new Vechicle();//v管理着Vechicle
Car c；
c=v;// 编译就不过，不行父类不能当作子类
c=(Car)v;//编译会过，但运行会出一个叫ClassCastException的异常


但：

Car cc=new Car();
v=cc;
Car ccc=(Car)v;//就可以，v实际上就是管理者Car
============

造型：不是类型转换



```



**造型：不是类型转换**,对象本身没有改变。



## 实例多态：方法覆盖



> 如果子类的方法覆盖了父类的方法，我们也说父类的那个方法在子类有了新的版本或者新的实现。覆盖的新版本具有与老版本相同的方法签名：相同的方法名称和参数表。因此，对于外界来说，子类并没有增加新的方法，仍然是在父类中定义过的那个方法。不同的是，这是一个新版本，所以通过子类的对象调用这个方法，执行的是子类自己的方法。

> **覆盖关系并不说明父类中的方法已经不存在了**，而是当通过一个子类的对象调用这个方法时，子类中的方法取代了父类的方法，父类的这个方法被“覆盖”起来而看不见了。而当通过父类的对象调用这个方法时，实际上执行的仍然是父类中的这个方法。注意我们这里说的是对象而不是变量，因为一个类型为父类的变量有可能实际指向的是一个子类的对象。

> <u>当调用一个方法时，究竟应该调用哪个方法，这件事情叫做绑定</u>。绑定表明了调用一个方法的时候，我们使用的是哪个方法。**绑定有两种：一种是早绑定，又称静态绑定，这种绑定在编译的时候就确定了；另一种是晚绑定，即动态绑定。动态绑定在运行的时候根据变量当时实际所指的对象的类型动态决定调用的方法。Java缺省使用动态绑定。**



### @Override



**方法名相同，参数相同**

• @Override //JDK1.5以后可以用这个注记来表示(不用也是可以的）
• void sayHello(){
• System.out.println("Hello! My name is " + name + ". My school is " + school );
• }
• 通过方法的覆盖，能够修改对象的同名方法的具体实现方法。

一个类中可以有几个同名的方法，这称为方法的重载（Overload）。
同时，还可以重载父类的同名方法。与方法覆盖不同的是，重载不要求参数
类型列表相同。 重载的方法实际是新加的方法。
















# 包

• package pkg1[.pkg2[.pkg3…]];
• 包及子包的定义，实际上是为了解决名字空间、名字冲突
它与类的继承没有关系。事实上，一个子类与其父类可以位于不同的包中。
• 包有两方面的含义
一是名字空间、存储路径（文件夹）、
一是可访问性（同一包中的各个类，默认情况下可互相访问）


>• 包层次的根目录是由环境变量CLASSPATH来确定的。
>• 在简单情况下，没有package语句，这时称为无名包（unnamed
>package）
>在Eclipse中，也叫(default package)。
>• Java的JDK提供了很多包
>java.applet，java.awt，java.awt.image，java.awt.peer，java.io，
>java.lang，java.net，java.util，javax.swing，等。

## import

>• 为了能使用Java中已提供的类，需要用import语句来导入所需要的类。
>• import语句的格式为：
>import package1[.package2…]. (classname |*);
>• 例如：
>import java.util.Date;
>• 这样，程序中 java.util.Date可以简写为Date
>import java.awt.*;
>import java.awt.event.*;
>注意：使用星号(*)只能表示本层次的所有类，不包括子层次下的类。
>• Java编译器自动导入包java.lang.*
>• Eclipse等IDE可以方便地生成import语句

## CLASSPATH

```
 在编译和运行程序中，经常要用到多个包，怎样指明这些包的根目录呢？
简单地说，包层次的根目录是由环境变量CLASSPATH来确定的。具体操作
有两种方法。
• 一是在java及javac命令行中，用-classpath（或-cp)选项来指明，如：
• java –classpath d:\tang\ch04;c:\java\classes;.
pk.TestPkg
• 二是设定classpath环境变量，用命令行设定环境变量，如：
• set classpath= d:\tang\ch04;c:\java\classes;.

```





## 常用包：

Java 语言中的常用包。
java.lang：这个包下包含了 Java 语言的核心类，如 String、 Math、 System 和 Thread 类等，使用
这个包下的类无须使用 import 语句导入，系统会自动导入这个包下的所有类。
java.util：这个包下包含了 Java 的大量工具类/接口和集合框架类/接口，例如 Arrays 和 List、 Set 等。
java.net：这个包下包含了一些 Java 网络编程相关的类/接口。
java.io：这个包下包含了一些 Java 输入/输出编程相关的类/接口。
java.text：这个包下包含了一些 Java 格式化相关的类。
java.sql：这个包下包含了 Java 进行 JDBC 数据库编程的相关类/接口。
java.awt：这个包下包含了抽象窗口工具集（Abstract Window Toolkits）的相关类/接口，这些类
主要用于构建图形用户界面（GUI）程序。
java.swing：这个包下包含了 Swing 图形用户界面编程的相关类/接口，这些类可用于构建平台无
关的 GUI 程序。 

# 访问控制符



• 修饰符（modifiers）分为两类
访问修饰符（access modifiers）
• 如public/private等
其他修饰符
• 如abstract等
• 可以修饰类、也可以修饰类的成员（字段、方法） 





| 修饰符                    | 同一个类中 | 同一个包中 | 不同包中的 子类 | 不同包中的 非子类 |
| ------------------------- | ---------- | ---------- | --------------- | ----------------- |
| private                   | Yes        |            |                 |                   |
| 默认 （包可访问）friendly | Yes        | Yes        |                 |                   |
| protected                 | Yes        | Yes        | Yes             |                   |
| public                    | Yes        | Yes        | Yes             | Yes               |





## 类的访问控制符

• 在定义类时，也可以用访问控制符。
• 类的访问控制符或者为public，或者默认。
若使用public，其格式为:
• public class 类名{
• ……
• }
如果类用public修饰，则该类可以被其他类所访问；
若类默认访问控制符，则该类只能被同包中的类访问。 



## setter 与 getter

• 将字段用private修饰，从而更好地将信息进行封装和隐藏。
• 用setXXXX和getXXXX方法对类的属性进行存取，分别称为setter与getter。
• 这种方法有以下优点
（1）属性用private更好地封装和隐藏，外部类不能随意存取和修改。

（2）提供方法来存取对象的属性，在方法中可以对给定的参数的合法性进行检验。
（3）方法可以用来给出计算后的值。
（4）方法可以完成其他必要的工作（如清理资源、设定状态，等等）。
（5）只提供getXXXX方法，而不提供setXXXX方法，可以保证属性是只读的。 



# 非访问控制符



| 基 本 含 义 | 修 饰 类               | 修 饰 成 员    | 修饰局部变量 |      |
| ----------- | ---------------------- | -------------- | ------------ | ---- |
| static      | 静态的、非实例的、类的 | 可以修饰内部类 | Yes          |      |
| final       | 最终的、不可改变的     | Yes            | Yes          | Yes  |
| abstract    | 抽象的、不可实例化的   | Yes            | Yes          |      |


## static
• 静态字段最本质的特点是：
它们是类的字段，不属于任何一个对象实例。
• 它不保存在某个对象实例的内存区间中，而是保存在类的内存区域的
公共存储单元。
• 类变量可以通过类名直接访问，也可以通过实例对象来访问，两种方
法的结果是相同的。
• 如System类的in和out对象，就是属于类的域，直接用类名来访问，
即System.in和System.out。

**static方法**：

• 用static修饰符修饰的方法仅属于类的静态方法，又称为类方法。
• 与此相对，不用static修饰的方法，则为实例方法。
• 类方法的本质是该方法是属于整个类的，不是属于某个实例的。
• 声明一个方法为static有以下几重含义。
• (1) 非static的方法是属于某个对象的方法，在这个对象创建时，对象的方法在内存中拥有自己专用的代码段。而static的方法是属于整个类的，它在内存中的代码段将随着类的定义而进行分配和装载，不被任何一个对象专有。

• (2) 由于static方法是属于整个类的，所以它不能操纵和处理属于某个对象的成员变量，而只能处理属于整个类的成员变量，即static方法只能处理本类中的static域或调用static方法。
• (3) static方法中，不能访问实例变量，不能使用this 或super。
• (4) 调用这个方法时，应该使用类名直接调用，也可以用某一个具体的对象名

>
>
> 静态初始化块的执行时机需要注意，它在类加载器第一次加载类时调用，不一定非要创建对象，例如使用类名.静态方法名。

## final

• 1．final类
如果一个类被final修饰符所修饰和限定，说明这个类不能被继承，即不可能有
子类。
• 2．final方法
final修饰符所修饰的方法，是不能被子类所覆盖的方法。

• 3．final字段及final局部变量
• final字段、 final局部变量(方法中的变量)
 它们的值一旦给定，就不能更改。
 是只读量，它们能且只能被赋值一次，而不能被赋值多次。
• 一个字段被static final两个修饰符所限定时，它可以表示常量，
 如Integer. MAX_VALUE(表示最大整数)、 Math.PI(表示圆周率)就是这种常量。
• 关于赋值
 在定义static final域时，若不给定初始值，则按默认值进行初始化（数值为0，boolean型为false，引用型为
null）。
 在定义final字段时，若不是static的域，则必须且只能赋值一次，不能缺省。
• 这种域的赋值的方式有两种：一是在定义变量时赋初始值，二是在每一个构造函数中进行赋值。
 在定义final局部变量时，也必须且只能赋值一次。它的值可能不是常量，但它的取值在变量存在期间不会改变。





final 关键字可用于修饰类、变量和方法， final 关键字有点类似 C#里的 sealed 关键字，用于表示它
修饰的类、方法和变量不可改变。 

> final 修饰变量时，表示该变量一旦获得了初始值就不可被改变， final 既可以修饰成员变量（包括类
> 变量和实例 Z 变量），也可以修饰局部变量、形参。有的书上介绍说 final 修饰的变量不能被赋值，这种
> 说法是错误的！严格的说法是， final 修饰的变量不可被改变，一旦获得了初始值，该 final 变量的值就不
> 能被重新赋值。 



Java 语

> 法规定： final 修饰的成员变量必须由程序员显式地指定初始值。 



归纳起来， final 修饰的类 Field、实例 Field 能指定初始值的地方如下。
¾ 类 Field：必须在静态初始化块中或声明该 Field 时指定初始值。
¾ 实例 Field：必须在非静态初始化块、声明该 Field 或构造器中指定初始值。 

### 修饰方法

final 修饰的方法不可被重写，如果出于某些原因，不希望子类重写父类的某个方法，则可以使用
final 修饰该方法。 



Java 提供的 Object 类里就有一个 final 方法： getClass()，因为 Java 不希望任何类重写这个方法，所
以使用 final 把这个方法密封起来。 



private final void test(){} 



### 修饰类

final 修饰的类不可以有子类，例如 java.lang.Math 类就是一个 final 类，它不可以有子类。
当子类继承父类时，将可以访问到父类内部数据，并可通过重写父类方法来改变父类方法的实现细
节，这可能导致一些不安全的因素。为了保证某个类不可被继承，则可以使用 final 修饰这个类。下面
代码示范了 final 修饰的类不可被继承。 

public final class FinalClass {} 





## abstract

• 1．abstract类
凡是用abstract修饰符修饰的类被称为抽象类。
抽象类不能被实例化
• 2．abstract方法
被abstract所修饰的方法叫抽象方法，抽象方法的作用在为所有子类定义一个统一的
接口。对抽象方法只需声明，而不需实现，即用分号（；）而不是用{}，格式如下：
abstract returnType abstractMethod( [paramlist] );
抽象类中可以包含抽象方法，也可以不包含abstract方法。但是，一旦某个类中包含
了abstract方法，则这个类必须声明为abstract类。
<u>*抽象方法在子类中必须被实现，否则子类仍然是abstract的。*</u>





# 设计原则

## 消除代码复制

>程序中存在相似甚至相同的代码块，是非常低级的代码质量问题。

代 码复制存在的问题是，如果需要修改一个副本，那么就必须同时修改所有其他的副本，否则就 存在不一致的问题。这增加了维护程序员的工作量，而且存在造成错误的潜在危险。很可能发 生的一种情况是，维护程序员看到一个副本被修改好了，就以为所有要修改的地方都已经改好 了。因为没有任何明显迹象可以表明另外还有一份一样的副本代码存在，所以很可能会遗漏还 没被修改的地方。

我们从消除代码复制开始。消除代码复制的两个基本手段，就是函数和父类。





## 耦合和聚合



> 要评判某些设计比其他的设计优秀，就得定义一些在类的设计中重要的术语，以用来讨论 设计的优劣。对于类的设计来说，有两个核心术语：<u>耦合和聚合</u>。 耦合这个词指的是类和类之间的联系。之前的章节中提到过，程序设计的目标是一系列通 过定义明确的接口通信来协同工作的类。耦合度反映了这些类联系的紧密度。我们努力要获得 低的耦合度，或者叫作松耦合（loose coupling）。



> 耦合度决定修改应用程序的容易程度。在一个紧耦合的结构中，对一个类的修改也会导致 对其他一些类的修改。这是要努力避免的，否则，一点小小的改变就可能使整个应用程序发生 改变。另外，要想找到所有需要修改的地方，并一一加以修改，却是一件既困难又费时的事情。 另一方面，在一个松耦合的系统中，常常可以修改一个类，但同时不会修改其他类，而且 整个程序还可以正常运作。



> 聚合与程序中一个单独的单元所承担的任务的数量和种类相对应有关，它是针对类或方法 这样大小的程序单元而言的理想情况下，一个代码单元应该负责一个聚合的任务（也就是说，一个任务可以被看作是 一个逻辑单元）。一个方法应该实现一个逻辑操作，而一个类应该代表一定类型的实体。聚合 理论背后的要点是重用：如果一个方法或类是只负责一件定义明确的事情，那么就很有可能在 另外不同的上下文环境中使用。遵循这个理论的一个额外的好处是，当程序某部分的代码需要 改变时，在某个代码单元中很可能会找到所有需要改变的相关代码段。



## 可扩展性



> 可扩展性的意思就是代码的某些部分不需要经过修改就能适应将来可能的变化。



## 框架加数据



> 从程序中识别出框架和数据，以代码实现框架，将部分功能以数据的方式加载，这样能在很大程度上实现可扩展性。





# 抽象，接口 interface

## 抽象类

> 我们用abstract关键字来定义抽象类。抽象类的作用仅仅是表达接口，而不是具体的实现细节。抽象类中可以存在抽象方法。抽象方法也是使用abstract关键字来修饰。抽象的方法是不完全的，它只是一个方法签名而完全没有方法体。



> **如果一个类有了一个抽象的方法，这个类就必须声明为抽象类。**如果父类是抽象类，那么子类必须覆盖所有在父类中的抽象方法，否则子类也成为一个抽象类。一个抽象类可以没有任何抽象方法，所有的方法都有方法体，但是整个类是抽象的。设计这样的抽象类主要是为了防止制造它的对象出来。





## 接口



* 接口是纯抽象类
  * 所有的成员函数，都是抽象函数
  * 所有的成员变量都是 public static final
* 接口规定了长什么样，但是不管里面有什么



```
public interface say(){
    
}

implements
```



* 类可以实现很多接口
* 接口可以继承接口，倒是不能继承类
* 接口不能实现接口

一个接口可以有多个直接父接口，但接口只能继承接口，不能继承类 

```
[修饰符] interface 接口名 extends 父接口 1, 父接口 2...
{
零个到多个常量定义...
零个到多个抽象方法定义...
}
```

接口的继承和类继承不一样，接口完全支持多继承，即一个接口可以有多个直接父接口。和类
继承相似，子接口扩展某个父接口，将会获得父接口里定义的所有抽象方法、常量 Field、内部类和
枚举类定义 

## 面向接口编程



* 设计程序时，先定义接口，再实现类
* **任何需要在函数间传入传出的一定是接口，而不是具体的类**
* java的优势啊，多人合作













• 接口，某种特征的约定
定义接口 interface
• 所有方法都自动是public abstract的
实现接口 implements
• 可以实现多继承
• 与类的继承关系无关
• 面向接口编程，而不是面向实现

>• 通常接口以able或ible结尾，表明接口能完成一定的行为。
>• 接口声明中还可以包括对接口的访问权限以及它的父接口列表。完整的接口声明如下：
>• [public] interface interfaceName [extends listOfSuperInterface]{
>• ……
>• }
>• 其中public指明任意类均可以使用这个接口，缺省情况下，只有与该接口定义在同一个包
>中的类才可以访问这个接口。
>• extends 子句与类声明中的extends子句基本相同，不同的是一个接口可以有多个父接口，
>用逗号隔开，而一个类只能有一个父类。子接口继承父接口中所有的常量和方法。

• 方法定义的格式为：
• returnType methodName ( [paramlist] )；
• 接口中只进行方法的声明，而不提供方法的实现，所以，方法定义没有方法体，且用分号(;)结尾。在接口中声明的方法具有public 和abstract属性。
所以定义的时候这两个关键词是可以省略的
• 另外，如果在子接口中定义了和父接口同名的常量或相同的方法，则
父接口中的常量被隐藏，方法被重载。


## 接口的实现

• 在类的声明中用implements子句来表示一个类使用某个接口，在类
体中可以使用接口中定义的常量，而且必须实现接口中定义的所有方
法。一个类可以实现多个接口。

## 接口类型

• 接口可以作为一种引用类型来使用。任何实现该接口的类的实例都可
以存储在该接口类型的变量中，通过这些变量可以访问类所实现的接
口中的方法。 Java运行时系统动态地确定该使用哪个类中的方法。
• 把接口作为一种数据类型可以不需要了解对象所对应的具体的类



## 实现了接口的类

一个类实现了一个或多个接口之后，这个类必须完全实现这些接口里所定义的全部抽象方法（也就
是重写这些抽象方法）；否则，该类将保留从父接口那里继承到的抽象方法，该类也必须定义成抽象类。 

```
[修饰符] class 类名 extends 父类 implements 接口 1,接口 2...
{
类体部分
}
```



# 异常处理



• 异常（exception ) 又称为例外、差错、违例
• 对应着Java运行错误处理机制 



```
try{
语句组
}catch(异常类名 异常形式参数名){
异常处理语句组；
}catch(异常类名 异常形式参数名){
异常处理语句组；
}finally{
异常处理语句组；
}


```

• finally语句
无论是否有异常都要执行
• 即使其中有break,return等语句
• 在编译时，finally部分代码生成了多遍 

• 一般所说的异常
• 是指Exception及其子类 

• 多异常的处理
子类异常要排在父类异常的前面 

## 拿到了异常



String getMessage()

String toString()

void printStackTrace()



## throw 与throws



## 自定义异常

### Throwable

• Throwable
Error: JVM的错误
Exception： 异常 



### Exception

• Exception分两种
RuntimeException及其子类，可以不明确处理
否则，称为受检的异常（checked Exception) 



• 受检的异常，要求明确进行语法处理
要么捕（catch）
要么抛（throws）：在方法的签名后面用throws xxxx来声明
• 在子类中，如果要覆盖父类的一个方法，若父类中的方法声明了
throws异常，则子类的方法也可以throws异常
• 可以抛出子类异常（更具体的异常），但不能抛出更一般的异常 



# 流



> 输入输出的方式。

流的基础类：作用的都是**字节**

1. InputStream
2. OutputStream





# 多线程

## volatile

> https://www.cnblogs.com/zhengbin/p/5654805.html
>
> Java语言提供了一种稍弱的同步机制，即volatile变量，用来确保将变量的更新操作通知到其他线程。当把变量声明为volatile类型后，编译器与运行时都会注意到这个变量是共享的，因此不会将该变量上的操作与其他内存操作一起重排序。volatile变量不会被缓存在寄存器或者对其他处理器不可见的地方，因此在读取volatile类型的变量时总会返回最新写入的值。

## Thread 类

> 1000毫秒，也就是一秒钟！

主要的两个方法

run（）:子类必须覆盖这个方法

start():会执行run()



sleep(毫秒) 会抛出异常：InterruptedException e 



## 线程的创建

线程：程序中单个顺序的流控制称为线程 



一个进程中可以含有多个线程
在操作系统中可以查看线程数
如：在Windows中，在任务管理器，右键，选择列，选中“线程数” 



一个进程中的多个线程
分享CPU（并发的或以时间片的方式）
共享内存（如多个线程访问同一对象） 



java.lang中的类 Thread 





## 线程体



• 线程体---- run()方法来实现的。
• 线程启动后，系统就自动调用run()方法。
• 通常，run()方法执行一个时间较长的操作
如一个循环
显示一系列图片
下载一个文件 





## 创建线程的两种方法





1. 通过Thread类创建线程

 ```
   new Thread(){
       public void run(){
           for(int i=0;i<10;i++)
           	System.out.println(i);
       }
   }.start();
 ```

   或用lambda表达式

   ```
   new Thread(()->{任务}).start()
   ```



2. 通过向Thread（Runnable）构造方法传递Runnable对象来创建线程


Runnable是个接口。给Thread这个构造用。


* 可使用匿名类来实现Runnable

```
class Counter implements Runnable {
	int id;
	Counter(int id){
		this.id = id;
	}
	public void run() {//必须实现这个方法
		int i=0;
		while( i++<=10 ){
			System.out.println("ID: " + id + "  No. " + i);
			try{ Thread.sleep(10); } catch( InterruptedException e ){}
		}
	}
}
```


## 线程的状态与生命周期

概览图：


• 线程的启动
start()

• 线程的结束（run方法做完了）
设定一个</u>标记变量</u>，以结束相应的循环及方法。

• 暂时阻止线程的执行
try{ Thread.sleep( 1000 );} catch( InterruptedException e ){ }





• 设定线程的优先级
setPriority( int priority)方法

MIN_PRIORITY，MAX_PRIORITY，NORM_PRIORITY 



**后台线程**



### 线程有两种

与虚拟机相关：

一类是普通线程（非Daemon线程）
• **在Java程序中，若还有非Demon线程，则整个程序就不会结束**

一类是Daemon线程（守护线程，后台线程）
• 如果普通线程结束了，则后台线程自动终止
• 注：垃圾回收线程是后台线程 

#### 把一个线程设为后台线程

方法：

setDaemon(true)



## 线程的同步



### 线程的不确定性

**同时运行的线程要共享数据**

转变为机器指令时，一条语句被解释为多条指令。



### 同步：解决方式，控制方式

考虑其它线程的状态与行为



> Java引入对象互斥锁的概念，保证共享数据操作的完整性。一种状态。
>
> * 互斥锁：每个对象都对应一个monitor(监视器)，上面有一个称为“互斥锁（lock,mutex)"的标记，这个标记用来表示在任一时刻，只能有一个线程能访问该对象。
> * synchronized:关键字，用来与对象的互斥锁联系。取得锁的这么一个过程。
>
> 比如，商城里的试衣间。



#### synchronized



```
* 对代码片段：
synchronized(对象){....}//取得对象的锁，才能进{}里面。其它线程是进不来的。{}结束了，就释放锁

* synchronized 放在方法声明中

• public synchronized void push(char c ){ 。。。。 }
• 相当于对synchronized(this), 表示整个方法为同步方法



```





### wait)(),notify(),notifyAll() 与对象锁

> 不是简单的锁住。等待，通知。

1. 在执行A时，需要等待别的资源或条件，等待别的对象释放锁，就需要等待，A在等待的时候，先把自己的那个锁释放掉给别人用。就使用wait（）方法：暂时释放对象锁。

2. B的线程使用notify()来告诉A，你可以接着走了，使其进入就绪状态



## **实例**：

```
生产者与消费者问题：


生产者：

private int data[] = new int[3];
private int index = 0;
public synchronized void put(int value) {
		while (index >= data.length) {//index代表有几个东西，满的时候就等待消费者来拿，没满就放进去
			try {
				wait(); // waits for notify() call from consumer
			} catch (InterruptedException e) {
			}
		}
		System.out.println("Producer " + " put: " + value);
		data[index] = value;
		index ++;
		notify();//执行到这里，说明我产生了东西了，通知消费者要不要来拿。
	}



消费者：
class CubbyHole {
	private int data[] = new int[3];
	private int index = 0;

	public synchronized int get() {
		while (index <= 0) {
			try {
				//消费者，没东西吃了，要个东西吃，就等待
				wait(); // waits for notify() call from Producer
			} catch (InterruptedException e) {
			}
		}
		index --;
		int value = data[index];
		System.out.println("Consumer " +  " got: " + data[index]);
		notify();//通知
		return value;
	}



----------------

class Producer extends Thread {
	private CubbyHole cubbyhole;
	private int number;

	public Producer(CubbyHole c, int number) {
		cubbyhole = c;
		this.number = number;
	}

	public void run() {
		for (int i = 0; i <10; i++) {
			cubbyhole.put(i);
			//System.out.println("Producer #" + this.number + " put: " + i);
			//try {
			//	sleep((int)(Math.random() * 100));
			//} catch (InterruptedException e) {
			//}
		}
	}
}

class Consumer extends Thread {
	private CubbyHole cubbyhole;
	private int number;

	public Consumer(CubbyHole c, int number) {
		cubbyhole = c;
		this.number = number;
	}

	public void run() {
		int value = 0;
		for (int i = 0; i <10; i++) {
			value = cubbyhole.get();
			//System.out.println("Consumer #" + this.number + " got: " + value);
		}
	}
}

class CubbyHole1
{
	private int seq;
	public synchronized int get() {
		return seq;
	}
	public synchronized void put(int value) {
		seq = value;
	}
}

class CubbyHole2
{
	private int seq;
	private boolean available = false;

	public synchronized int get() {
		while (available == false) ; //dead locked !!!
		return seq;
	}
	public synchronized void put(int value) {
		while (available == true) ;
		seq = value;
		available = true;
	}
}

class CubbyHole3 {
	private int seq;
	private boolean available = false;

	public synchronized int get() {
		while (available == false) {
			try {
				wait(); // waits for notify() call from Producer
			} catch (InterruptedException e) {
			}
		}
		available = false;
		notify();
		return seq;
	}

	public synchronized void put(int value) {
		while (available == true) {
			try {
				wait(); // waits for notify() call from consumer
			} catch (InterruptedException e) {
			}
		}
		seq = value;
		available = true;
		notify();
	}
}


class CubbyHole {
	private int data[] = new int[3];
	private int index = 0;

	public synchronized int get() {
		while (index <= 0) {
			try {
				wait(); // waits for notify() call from Producer
			} catch (InterruptedException e) {
			}
		}
		index --;
		int value = data[index];
		System.out.println("Consumer " +  " got: " + data[index]);
		notify();
		return value;
	}

	public synchronized void put(int value) {
		while (index >= data.length) {
			try {
				wait(); // waits for notify() call from consumer
			} catch (InterruptedException e) {
			}
		}
		System.out.println("Producer " + " put: " + value);
		data[index] = value;
		index ++;
		notify();
	}
}

class ProducerConsumerStack {
	public static void main(String args[]) {
		CubbyHole c = new CubbyHole();
		Producer p1 = new Producer(c, 1);
		Consumer c1 = new Consumer(c, 1);
		p1.start();
		c1.start();
	} 
}

```



## 并发api

### 原子变量及线程安全的集合

java.util.concurrent包及其子包。提供一些东西更好的操作线程。

里面有单变量，集合，Timer，线程池

**原子变量**：java.util.concurrent.atomic包

* AtomicInteger类，原子整数
* 上类有个getAndIncrement()方法//安全的，不会像n++那样执行到一半就被其它线程那去了。

**集合**：ArrayList与HashMap在线程里也是不安全的。不一致性问题。

* Vector/HashTable是安全的

jdk 1.5以后：对于集合，java.util.concurrent.包增加了一些类，以便更灵活的使用锁机制。

* CopyOnWriteArrayList、 CopyOnWriteArraySet
  **适合于很少写入而读取频繁的对象** 
* ConcurrentHashMap//映射
  putIfAbsent(), remove(), replace()
*  ArrayBlockingQueue//队列
    生产者与消费者，使用put()及take() //wait()或notify()已经帮我们实现好了，不用从底层实现了。



### 线程池

> 每开一个线程，系统就要为它建一些环境，相应的机制，开销是很大的。并不是线程越多，程序运行越快。
>
> 线程池，一个线程执行完毕，并没有被销毁掉。线程池里有一些线程。
>
> 线程池相关的类：
>
> * ExecutorService 接口、 ThreadPoolExecutor 类 
> * Executors 工具类
>
> 用法：
>
> * ExecutorService pool = Executors.newCachedThreadPool(); 创建一个线程池
> * 使用pool.execute( Runnable r)方法,收一个Runnable对象
> * pool. shutdown()关闭线程池。

线程池相关的类
ExecutorService 接口、 ThreadPoolExecutor 类
Executors 工具类 

### Timer

> 两个Timer：底层是一个线程，循环的执行任务
>
> * java.util.Timer类重复某件事，计时器
> * javax.swing.Timer类，重复执行ActionListener



### 线程中对图形界面的更新

要调用：SwingUtilites.invokeLater (Runnable r)



## 流式操作及并行流

> java8开始提供的新特性。

**为什么要有这么个特性**：

# 反射

https://www.sczyh30.com/posts/Java/java-reflection-1/





# NIO



https://tech.meituan.com/nio.html



# java  特性



## 内部类 Inner class

**定义**：

将类B的定义class xxxx{…}置入一个A类的内部即可
编译器生成A$B这样的class文件
内部类不能够与外部类同名 

**使用**：

* 类A里面用：**与普通类的使用方式相同 **
* 在其他地方使用 ，不在A类使用。
  * 类名前要冠以外部类的名字。 A.B.XXX
  * 在用new创建内部类实例时，也要在 new前面冠以对象变量。
    • 外部对象名A.new 内部类名(参数) 

* 内部类中使用外部类的成员
  * 内部类中可以直接访问外部类的字段及方法
    即使private也可以 
  * 如果内部类中有与外部类同名的字段或方法，则可以用
    外部类名.this.字段及方法 

### 内部类的修饰符

> 内部类B也是类A的一个成员。
>
> * 访问控制符：public,protected,默认及private。
>   • 注：外部类只能够使用public修饰或者默认 
> * final,abstract 

### static

用static修饰内部类 表明该内部类实际是一种外部类
因为它与外部类的实例无关
有人认为static的类是嵌套类（nested class），不是内部类inner class 



**static类在使用时** ：

1、实例化static类时，在 new前面不需要用对象实例变量；
2、 **static类中不能访问其外部类的非static的字段及方法，既只能够访问static成员。**
3、 static**方法中不能访问非static的域及方法**，也**不能够不带前缀地new 一个非**
**static的内部类**

## lambda表达式，方便你写

> **java 8新增语法。**
>
> （λ expression) 
>
> 相当与一个函数。在Java里相当与匿名类的一个实例。

**写法**：`(参数)->结果`

* (String s)->s.length()//参数有类型
* (x)->x*x//参数类型都省略了
* ()->{}//参数都没有



**<u>起因</u>**：

```
Runnable doIt = new Runnable(){//匿名类，实现了这个Runnable接口。
	public void run(){//必须实现的方法。
	System.out.println("aaa");
	}
};
new Thread( doIt ).start();//线程需要一个Runnable对象，自己有start（）方法。

使用lambda表达式：
Runnable doIt = () ->System.out.println("aaa");//()就是哪个run方法
new Thread( doIt ).start();

甚至是：new Thread(() ->System.out.println("aaa") ).start();//直接放在Thread的构造里

```

> 可以看出：Lambda表达式是接口或者说是接口函数的简写 
>
> 把匿名类更加简写。

### 实例：

> 求积分：interface Fun { double fun( double x );} 接口

```
double Integral(Fun fun,.....)
{
	。。。。。
}
一开始要这样写：
double d = Integral( new Fun(){
	public double fun(double x){
	return Math.sin(x);
	}
}, 0, Math.PI, 1e-5 );

使用lambda

double d = Integral( x->Math.sin(x),
0, Math.PI, 1e-5);
```

## 使用lambda的条件

> 由于Lambda**只能表示一个函数**，所以 
>
> 能写成Lambda的**接口要求包含且最多只能有一个抽象函数** ,自动对应到唯一的抽象函数去了。
>
> 把代码当做数据，一定程度上实现了函数式编程。

这样的接口可以（但不强求）用注记
@FunctionalInterface 来表示。**称为函数式接口** 

如

```

@FunctionalInterface
interface Fun { double fun( double x );} 
```



## 范型

> 泛型（Generic）是JDK1.5增加的最重要的Java语言特性。 

**使用泛型可以针对不同的类有相同的处理办法**
• Vector<String> v = new Vector<String> ();
• v.addElement( “one” );
• String s = v.elementAt(0); 





使用泛型的好处
• 类型更安全
• 适用更广泛，针对不同的类有相同的处理办法，但这些类之间不一定有继承关系。 







# 深入理解面向对象





## 抽象类与接口

1. 抽象类：
----

> 一个类里有抽象方法就必须是个抽象类。

> 抽象类中可以包含**具体的方法**，当然也可以不包含抽象方法。

> 非抽象类中不可以有抽象方法。所以一个非抽象类继承了一个抽象类，必须实现父类所有抽象方法。



https://www.cnblogs.com/chenssy/p/3376708.html

> **抽象类不能被实例化，实例化的工作应该交由它的子类来完成，它只需要有一个引用即可**



2. 接口：
----

> 同时实现该接口的实现类必须要实现该接口的所有方法，通过使用implements关键字，他表示该类在遵循某个或某组特定的接口，同时也表示着“interface只是它的外貌，但是现在需要声明它是如何工作的”。

> 实现接口的非抽象类必须要实现该接口的所有方法。抽象类可以不用实现。









## 对象 引用和指针



Person p = new Person();，这行代码创建了一个
Person 实例，也被称为 Person 对象，这个 Person 对象被赋给 p 变量。 

当一个对象被创建成功以后，这个对象将保存在堆内存中， Java 程序不允许直接访问堆内存中的对
象，只能通过该对象的引用操作该对象。也就是说，不管是数组还是对象，都只能通过引用来访问它们。



>这里的关键是理解类的定义和对象的关系，理解对象中的成员变量是怎么来的，怎么就能让成员函数明白自己在和哪个对象打交道。


在没有引入类之前，变量是跟着代码走的。代码写到哪儿，变量写在哪里，那么运行的时候变量就在那儿。现在，写在类里的成员变量，只是一个声明，变量并不在那里，变量不在类里，变量在每一个对象里。



建议你一定要跟着视频中的方法自己用调试的方法看几遍成员函数的执行，做各种尝试，一定要正确而且充分地理解这里的关系。



>**变量初始值**：
>变量的初始化是程序安全很重要的一环。一旦创建了一个对象，有什么手段可以保证其中的每一个成员变量都有确定的初始值呢？
>Java提供了多种手段来保障对象创建时的初始化，包括给每个成员变量默认的“0”值、定义初始化和构造函数。


**对象交互**
>面向对象程序设计的第一步，就是在问题领域中识别出有效的对象，然后从识别出的对象中抽象出类来。面对纷繁复杂的现实问题，往往存在多种对象划分的方式，而不同的划分会带来类的设计以至于程序结构的各种不同。
>一个对象当然可以由其他类的对象来组成，就像一个人体里面有心脏、肠胃一样。对象是由其他对象组成的，而类定义了这样的组合关系。



>那么下一个问题，就是当一个对象里有多个对象的时候，那些对象之间是如何交互的，对象和对象之间的联系是如何建立的，对象如何和其他对象交流。对象和对象之间的联系紧密程度叫做耦合。对象和对象的耦合程度越紧，表现在源代码上，就是它们的代码是互相依赖、互相牵制的。我们理想的模型，是对象和对象之间的耦合要尽可能的松，平行的对象要尽量减少直接联系，让更高层次的对象来提供通信服务。



**封装**：
>封装，就是把数据和对这些数据的操作放在一起，并且用这些操作把数据掩盖起来，是面向对象的基本概念之一，也是最核心的概念。

我们有一个非常直截了当的手段来保证在类的设计的时候做到封装：

所有的成员变量必须是private的，这样就避免别人任意使用你的内部数据；

所有public的函数，只是用来实现这个类的对象或类自己要提供的服务的，而不是用来直接访问数据的。除非对数据的访问就是这个类及对象的服务。简单地说，给每个成员变量提供一对用于读写的get/set函数也是不合适的设计。



**包**：
>当你的程序越来越大的时候，你就会需要有一个机制帮助你管理一个工程中众多的类了。包就是Java的类库管理机制，它借助文件系统的目录来管理类库，一个包就是一个目录，一个包内的所有的类必须放在一个目录下，那个目录的名字必须是包的名字。

你可以忽略不看包，反正一切靠Eclipse。但是作为一个Java程序员，你不能不懂包。要不然，在使用别人的类库和部署你的程序的时候，会遇到不少莫名其妙的麻烦。

因为，包治百病啊！


**类变量**：
>类是描述，对象是实体。在类里所描述的成员变量，是位于这个类的每一个对象中的。

>而如果某个成员有static关键字做修饰，它就不再属于每一个对象，而是属于整个类的了。

通过每个对象都可以访问到这些类变量和类函数，但是也可以通过类的名字来访问它们。类函数由于不属于任何对象，因此也没有办法建立与调用它们的对象的关系，就不能访问任何非static的成员变量和成员函数了。

**方法**：属于类

**static**:

如果在 static 修饰的方法中使用 this
关键字， 则这个关键字就无法指向合适的对象。 所以， static 修饰的方法中不能使用 this 引用。 由于 static
修饰的方法不能使用 this 引用， 所以 static 修饰的方法不能访问不使用 static 修饰的普通成员， 因此 Java
语法规定：静态成员不能直接访问非静态成员 



## 构造器

> 构造器不是没有返回值吗？为什么不能void 修饰？？
> >简单地说， 这是 Java 的语法规定。 实际上，
类的构造器是有返回值的，当我们用 new 关键字来调用构造器时，构造器返回该类的实例，可以把这个类的实例当成构造器的返回值， 因此构造器的返回值类型总是当前类，无须定义返回值类型。但必须注意：不能在构造器里显式使用 return 来返回当前类的对象，因为构造器的返回值是隐式的。



>如果程序员没有为 Java 类提供任何构造器，则系统会为这个类提供一个无参数的构
>造器，这个构造器的执行体为空，不做任何事情。无论如何， Java 类至少包含一个构造器。 
>


>一旦程序员提供了自定义的构造器，系统就不再提供默认的构造器
>

>因为构造器主要用于被其他方法调用，用以返回该类的实例，因而通常把构造器设置成 public 访问
权限，从而允许系统中任何位置的类来创建该类的对象。除非在一些极端的情况下，我们需要限制创建该类的对象，可以把构造器设置成其他访问权限，例如设置为 protected，主要用于被其子类调用；把其设置为 private，阻止其他类创建该类的实例。





# Object类



## 方法



### toString()


```
public String toString(){

return "";
    
}

当使用System.out.println(对象)；时，自动调用toString()方法
```



### equals()



判断是否为同管理一个对象





# 控制反转与MVC



GUI（图形用户界面）给应用程序提供界面,其中包括窗口、菜单、按钮和其他图形组件,这就是今天大多 数人所熟悉的“典型”应用程序界面。

图形用户界面所涉及的细节很多,我们的课程并不打算教授GUI，但是我们打算借助GUI来介绍两个设计思想：控制反转和MVC设计模式。

部件是创建GUI的独立部分,比如像按钮、菜单、菜单项、选择框、滑动条、文本框等。Java类库中有不少现成的部件。


## 布局

>布局是指如何在屏幕上放置组件。过去,大多数简单的GUI系统让程序员在二维坐标系上 指定每个组件的x和y坐标(以像素点为单位),这对于现代的GUI系统来说太简单了。因为现代的GUI系统还得考虑不同的屏幕分辨率、不同的字体、用户可改变的窗口尺寸,以及许多其他使得布局困难的因素。所以需要有一种能更通用地指定布局的方法,比如,要求“这个部件应该在那个部件的下面“或者”这个部件在窗口改变尺寸时能自动拉伸,但是其他部件保持尺寸不变”。这些可以通过布局管理器(layout manager)来实现。

**事件**：


事件处理是用来响应用户输入的技术。创建了部件并且放在屏幕上合适的位置以后,就得 要有办法来处理诸如用户点击按钮这样的事情。Java类库处理这类事情的模型是基于事件的。 如果用户激活了一个部件(比如,点击按钮或者选择菜单项),系统就会产生一个事件。应用 程序可以收到关于这个事件的通知(以程序的一个方法被调用的方式),然后就可以采取程序该做的动作了。

## 控制反转/注入反转

**swing**:
Swing使用一个非常灵活的模型来处理GUI的输入:采用事件监听器的事件处理(event handling)模型。

Swing框架本身以及大部分部件在发生一些情况时会触发相关的事件,而其他的对象也许会对这些事件感兴趣。不同类型的动作会导致不同类型的事件。当点击一个按钮或选中一个菜单项,部件就会触发动作事件;而当点击或移动鼠标时,会触发鼠标事件;当框架被关闭或最小化时,会触发窗口事件。另外还有许多种其他事件。

所有的对象都可以成为任何这些事件的监听器,而一旦成为监听器,就可以得到这些事件触发的通知。

实现了众多监听器接口之一的对象就成为一个事件监听器。如果对象实现了恰当的接口, 就可以注册到它想监听的组件上。

**内部类**：

内部类就是指一个类定义在另一个类的内部，从而成为外部类的一个成员。因此一个类中可以有成员变量、方法，还可以有内部类。实际上Java的内部类可以被称为成员类，内部类实际上是它所在类的成员。所以内部类也就具有和成员变量、成员方法相同的性质。比如，成员方法可以访问私有变量，那么成员类也可以访问私有变量了。也就是说，成员类中的成员方法都可以访问成员类所在类的私有变量。**内部类最重要的特点就是能够访问外部类的所有成员。**

>内部类又分为成员内部类
>函数内部类，匿名类

Swing的消息机制广泛使用匿名类

## MVC

M

V

C

>C与V逻辑上是没有关系的，C不知道V，C只通知M，V会去M那得到所有数据，重新画一遍，不关心具体细节。
>**V常常与C合并在一起。**

# 问题

## javase

### 构造器问题

> 问：一个类中的静态方法可以访问构造方法？
>
> 答：`分清楚是new Object(),还是Object()`

# 算法



## 辗转相除法 求最大公约数

这里有两个数 u,v，求最大公约数

```
int u=32;
int v=26;
while(v!=0){
    int temp=u%v;
    u=v;
    v=temp;
}
System.out.println(u);





```

1. 如果v=0,u就是最大公约数；
2. 否则，计算u除以v的余数，让u等于v，而v等于那个余数。
3. 直到第一步。









# 资料



## 博客

### 这个厉害

阿里巴巴，可投简历：

实在厉害

https://www.hollischuang.com/







# 项目1：坦克大战

https://blog.csdn.net/zhujunxxxxx/article/details/40460931

http://qq-24665727.iteye.com/blog/2261314