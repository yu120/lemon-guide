<div style="color:#16b0ff;font-size:50px;font-weight: 900;text-shadow: 5px 5px 10px var(--theme-color);font-family: 'Comic Sans MS';">Interview</div>

<span style="color:#16b0ff;font-size:20px;font-weight: 900;font-family: 'Comic Sans MS';">Introduction</span>：收纳面试知识总结！

[TOC]

# JAVA

**问题：JDK 和 JRE 有什么区别？**

- JDK：Java Development Kit 的简称，Java 开发工具包，提供了 Java 的开发环境和运行环境
- JRE：Java Runtime Environment 的简称，Java 运行环境，为 Java 的运行提供了所需环境

具体来说 JDK 其实包含了 JRE，同时还包含了编译 Java 源码的编译器 Javac，还包含了很多 Java 程序调试和分析的工具。简单来说：如果你需要运行 Java 程序，只需安装 JRE 就可以了，如果你需要编写 Java 程序，需要安装 JDK。



**问题：== 和 equals 的区别是什么？**

`==` 对于`基本类型`来说是`值比较`，对于`引用类型`来说是`比较引用地址`。而 `equals` 默认情况下是`引用比较`（Object中`public boolean equals(Object obj) {return (this == obj);}`），只是很多类重新了 equals 方法，比如 `String`、`Integer` 等把它变成了值比较，所以一般情况下 `equals` 是`比较值是否相等`。



**问题：两个对象的 hashCode() 相同，则 equals() 也一定为 true，对吗？**

不对，两个对象的 hashCode() 相同，equals() 不一定 true。



**问题：String 属于基础的数据类型吗？**

String不属于基础类型，基础类型有8种：byte、boolean、char、short、int、float、long、double，而String属于对象。



**问题：String、StringBuffer、StringBuilder的区别？**

String 声明的是不可变的对象，每次操作都会生成新的 String 对象，然后将指针指向新的 String 对象。StringBuffer 是线程安全的，而 StringBuilder 是非线程安全的；但 StringBuilder 的性能却高于 StringBuffer，所以在单线程环境下推荐使用 StringBuilder，多线程环境下推荐使用 StringBuffer。



**问题：String str="ABC"与 String str=new String("ABC")一样吗？**

不一样，因为内存的分配方式不一样。String str="ABC"的方式Java 虚拟机会将其分配到常量池中；而 String str=new String("ABC") 则会被分到堆内存中。



**问题：如何将字符串反转？**

使用 `StringBuilder` 或者 `StringBuffer` 的 `reverse()` 方法。



**问题：String 类的常用方法都有那些？**

- indexOf()：返回指定字符的索引
- charAt()：返回指定索引处的字符
- replace()：字符串替换
- trim()：去除字符串两端空白
- split()：分割字符串，返回一个分割后的字符串数组
- getBytes()：返回字符串的 byte 类型数组
- length()：返回字符串长度
- toLowerCase()：将字符串转成小写字母
- toUpperCase()：将字符串转成大写字符
- substring()：截取字符串
- equals()：字符串比较



**问题：Java 中 IO 流分为几种？**

按功能来分：输入流（input）、输出流（output）。按类型来分：字节流和字符流。字节流和字符流的区别是：字节流按 8 位传输以字节为单位输入输出数据，字符流按 16 位传输以字符为单位输入输出数据。
