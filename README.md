# lemon-guide

收纳`操作系统`、`JAVA`、`算法`、`数据库`、`中间件`、`解决方案`、`架构`、`DevOps`和`大数据`等技术栈总结！



# [1 OS](OS.md)

提供OS



# [2 JAVA](JAVA.md)

提供JAVA



# [3 Algorithm](Algorithm.md)

提供Algorithm



# [4 Database](Database.md)

提供Database



# [5 Middleware](Middleware.md)

提供Middleware



# [6 Solution](Solution.md)

提供Solution



# [7 Architecture](Architecture.md)

提供Architecture



# [8 DevOps](DevOps.md)

本章节主要总结并收纳了常用的JDK工具、Linux命令、Shell语法、Git命令、测试工具、Docker等。

## 8.1 JDK Tools

![Visual-GC](images/README/Visual-GC.png)

![jfr-code](images/README/jfr-code.jpg)

- **jps**：用于查看JAVA进程编号
- **jstat**：用于打印GC回收统计信息，便于分析是否出现FGC等情况
- **jstack**：用于dump出指定进程中的线程堆栈快照信息，便于排查应用是否有锁、死锁或排查CPU占比高的线程代码
- **jmap**：用于dump出指定进程中当前内存的快照信息，便于分析内存的内容结构，从而定位内存泄漏等问题
- **jhat**：用于与jmap搭配使用，用来分析jmap生成的dump
- **jconsole**：Java GUI监视工具，可以以图表化的形式显示各种数据，并可通过远程连接监视远程的服务器VM
- **jvisualvm**：一个基于图形化界面的，可以查看本地及远程的JAVA GUI监控工具，可以查看CPU、堆、线程、GC等
- **jmc**：JDK自带图形界面监控工具。JMC打开性能日志后可查看**一般信息、内存、代码、线程、I/O、系统、事件** 功能
- **EclipseMAT**：基于Eclipse内存分析工具，它可以帮助我们查找内存泄漏和减少内存消耗



## 8.2 Linux Command

![htop](images/README/htop.png)

- **基本命令**：`vi/vim`、`scp`、`tar`、`su`、`df`、`tail`、`grep`、`awk`、`find`、`netstat`、`echo`、`telnet`、`rpm`、`yum`等
- **监控命令**
  - **Memory**：`free`、`vmstat`
  - **CPU**：`top`、`htop`、`sar`
  - **IO**：`iostat`、`pidsta`、`iotop`
  - **Network**：`netstat`、`iftop`、`tcpdump`
  - **Others**：`dstat`、`saidar`、`Glances`
- **瓶颈排查**：定位线上最耗CPU的线程、定位丢包错包情况、查看网络错误、包的重传率等



## 8.3 Shell

收纳了Shell脚本的变量、数组、算术运算、字符串、条件判断、流程控制等基本语法，学完后就可自己写Shell脚本。



## 8.4 Git

收纳了Git相关的常用命令，如：`git clone`、`git add`、`git rm`、`git commit`、`git branch`、`git tag`、`git push`、`git pull`、`git log`、`git remote`、`git fetch`、`git reset`等。



## 8.5 Test Tools

![Junit-Summary-Report](images/README/Junit-Summary-Report.png)

- **AB**：ApacheBench (ab)是 Apache 网站服务器软件附带的工具，专门用来做HTTP接口的性能测试
- **Jmeter**：Apache JMeter是Apache组织开发的基于Java的压力测试工具。用于对软件做压力测试



## 8.6 Docker



# [9 BigData](BigData.md)

提供BigData



# [10 Others](Others.md)

提供Others 

