> [返回目录](https://github.com/Crab2died/jdepth)

#                                               GC

## 一. Java虚拟机内存区域
### 1. 运行时数据区
   ![java运行时数据区](https://raw.githubusercontent.com/Crab2died/jdepth/master/src/main/java/com/github/jvm/java%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84.png)

### 2. 程序计数器(Program Counter Register)
   - 1、程序计数器是线程内(每个线程都有唯一的、封闭的)一小块内存区域
   - 2、计数器指定的是当前虚拟机执行指令的地址
   - 3、当虚拟机执行的是Native方法时，计数器值为空(Undefined),此内存区域是唯一一个在Java虚拟机规范中没有规定任何OutOfMemoryError
        情况的区域。

### 3. Java虚拟机栈(Java Virtual Machine Stacks)
   - 1、虚拟机栈是线程内部的、封闭的
   - 2、虚拟机栈描述的是java方法执行的内存模型
   - 3、每个方法在执行的同时都会创建一个栈帧(Stack Frame)用于存储局部变量表、 操作数栈、 动态链接、 方法出口等信息
   - 4、java方法的执行就是入栈与出栈的过程
   - 5、如果虚拟机栈深度超出了虚拟机允许深度将会抛出StackOverflowError异常,现代虚拟机大多数支持动态扩展(也允许固定长度),当虚拟机申
        请扩展时申请不到足够的内存时,将会抛出OutOfMemoryError异常
   
### 4. 本地方法栈(Native Method Stack)
   - 1、为虚拟机调用本地Native方法提供服务
   - 2、也有虚拟机(譬如Sun HotSpot虚拟机)直接就把本地方法栈和虚拟机栈合二为一
   - 3、也会抛出StackOverflowError异常和OutOfMemoryError异常

### 5. Java堆(Java Heap) GC堆
   - 1、线程共享的最大一块内存区域
   - 2、此内存区域的唯一目的就是存放对象实例，几乎所有的对象实例都在这里分配内存，虚拟机规范所有的对象实例与数据都在堆上分配
   - 3、随着JIT编译器的发展与逃逸分析技术逐渐成熟，栈上分配、 标量替换优化技术将会导致一些微妙的变化发生，所有的对象都分配在堆上也渐渐
        变得不是那么“绝对”了

### 6. 方法区(Method Area)

> [返回目录](https://github.com/Crab2died/jdepth)