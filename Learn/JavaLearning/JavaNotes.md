# Java学习笔记

## 1 基础阶段

### 0 面试题

#### 1 Java语言有哪些特点?

1. 简单易学；
2. 跨平台
3. 安全性
4. 高效性
5. 面向对象（封装、继承、多态）
6. 可靠性
7. 解释与编译并存
8. 强大的生态

#### 2 什么是字节码?采用字节码的好处是什么? ^[源于JavaGuide]

在Java中，JVM能理解的代码就是字节码（即后缀为 `.class` 的文件），该文件不面向任何特定的处理器，只面向虚拟机。通过字节码，解决了传统解释型语言执行效率低的问题，同时又兼顾了可移植性

![Java源码转成机器码的过程](images/2024-02-06-11-22-14.png "Java源码转成机器码的过程")



### 1.1 Java文件的编译与运行

Java文件的运行过程：

1. 编写。编写Java源文件
2. 编译。在控制台中使用命令 `javac 源文件名.java` 编译源文件，编译后生成一个**源文件名.class**字节码文件
3. 运行。在控制台中使用命令 `java 源文件名` 运行class文件，注意在该步骤中不需要加入class文件后缀

### 1.2 变量与运算符

长整型(long)数值有一个后缀 `l` 或 `L`

float型数值有一个后缀 `f` 或 `F`

取余运算中，如果有负数参与，则结果与被模数的符号保持一致:

结合赋值: `+=` `-=` `*=` `/*` `%=` 存在这样一种情况，运算得到的值与左侧操作数类型不同时，会发生强制转换

```Java
int x = 3;

x += 3.5; // 相当于 x = (int)(x + 3.5),该行语句不会发生报错
```

逻辑运算符 & 和 && 的区别：

一旦遇到false的情况，&&不会继续判断剩余的情况，直接返回false，而 & 仍会继续判断

### 1.3 流程控制

#### 使用Scanner类从键盘获取输入：

1. 引入相关的包: `import java.util.Scanner;` 
2. 声明一个Scanner对象：`Scanner sc = new Scanner(System.in);`
3. 根据输入的数据类型调用相应的类：
   
   ```java
    import java.util.Scanner;
    Scanner sc = new Scanner(System.in);

    int numInt = sc.nextInt();
    double numDouble = sc.nextDouble();
    String name = sc.next();
    char c = sc.next().charAt(0);// 输入一个字符
   ```

需要注意的是，Scanner类并没有定义读取字符的方法，因此当我们需要读取一个字符时，可以这么做 `sc.next().charAt(0)`

#### 如何获取一个随机数?

1. 使用Math类中的random()方法
2. 获取某个范围内的整数：`int num = (int)(min + Math.random() * (max - min + 1));`

#### break语句

在多层循环的嵌套中，break语句可以通过 `break 标签名` 来退出指定的循环，但在开发中不推荐这么使用

### 1.4 数组

#### 使用方式1-动态初始化

可以这样定义数组：

![数组的动态初始化](images/2024-03-01-10-42-53.png)

完成数据的输入并用数组存放：

```Java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        double[] scores = new double[5];

        Scanner input = new Scanner(System.in);
        for (int i = 0; i < scores.length; i++) {
            System.out.println("请输入第" + i + "个数:");
            scores[i] = input.nextDouble();
        }

        for (int i = 0; i < scores.length; i++) {
            System.out.println("输出:");
            System.out.println("scores[" + i + "] = " + scores[i]);
        }

    }

}
```

#### 使用方式2-先声明再分配

```Java
int[] nums; // 先声明数组nums
nums = new int[5]; // 再动态分配空间
```

#### 使用方式3-静态初始化

![数组的静态初始化](images/2024-03-01-10-51-30.png)

## 2 面向对象编程

### 2.1 基础

![图2-1 类与对象的关系示意图](images/2024-03-01-11-33-52.png)

类是抽象的、概念的

对象是具体的、实际的

#### 属性与成员变量

![图2-2 属性与成员变量](images/2024-03-01-12-00-35.png)

属性和成员变量是一样的，属性可以是基本数据类型，也可以是引用类型如数组、对象

![图2-3 属性的细节说明](images/2024-03-01-12-09-50.png)

属性的定义多了一个**访问修饰符**，用来控制属性的访问范围，访问修饰符有4种：

* public
* protected
* 默认
* private

#### 创建对象

![图2-4 创建对象的两种方法](images/2024-03-01-12-15-11.png)