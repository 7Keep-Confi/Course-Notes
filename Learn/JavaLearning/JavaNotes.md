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

#### 类与对象的内存分配机制

![图2-5 类与对象的内存分配机制](images/2024-03-01-16-11-22.png)

内存结构分析：

* 栈：一般是用来存放基本数据类型如局部变量
* 堆：存放对象
* 方法区：常量池（常量例如字符串）、加载类信息（属性信息、方法信息）

创建对象的流程分析：

1. 首先，加载类信息（属性信息和方法信息）
2. 为相应的类在堆中分配空间并进行默认初始化
3. 把地址赋给指定的对象
4. 进行指定初始化

#### 成员方法的细节说明

![图2-6 成员方法返回数据类型说明](images/2024-03-01-17-07-43.png)

一个方法最多有一个返回值，如果需要返回多个结果，可以考虑使用数组（注意此时的方法类型也要定义为数组类型）

![图2-7 形参列表](images/2024-03-01-17-11-47.png)

形参：形式参数，方法定义时的参数

实参：实际参数，调用方法时的参数

![图2-8 方法不能嵌套定义](images/2024-03-01-17-15-54.png)

不能在方法中再定义方法

![图2-9 方法的调用细节1](images/2024-03-01-17-19-28.png)

在同一个类中的方法可以**直接调用**，即不需要先创建对象再进行调用

![图2-10 方法调用细节2](images/2024-03-01-17-30-51.png)

跨类的方法调用需要使用对象名调用，并且还与所要调用方法的访问修饰符有关

``` Java
public class Main {
    public static void main(String[] args) {
       A a1 = new A();
       a1.m1();
    }

}

class A {
    public void m1(){
        System.out.println("A类中的方法m1()被调用！");
        B b1 = new B();
        b1.hi();
        System.out.println("A类中的方法m1()继续执行....");
    }
}

class B {
    public void hi(){
        System.out.println("B类中的方法hi()被调用！");
    }
}
```

上面这段程序的输出结果如下：

![图2-11 跨类方法调用程序输出结果](images/2024-03-01-17-33-15.png)

#### 重载

##### 1 理解

在Java中，同一个类允许存在多个**同名**的方法，但要求**形参列表不一致**

重载案例：

```Java
public class Main {
    public static void main(String[] args) {
       MyCalculator mc = new MyCalculator();
       System.out.println(mc.calculate(2, 4));
       System.out.println(mc.calculate(2, 3.2));
       System.out.println(mc.calculate(3.4, 3));
       System.out.println(mc.calculate(3, 2, 1));
    }

}

class MyCalculator {
    public int calculate(int n1, int n2){
        System.out.println("public int calculate(int n1, int n2)被运行...");
        return n1 + n2;
    }

    public double calculate(int n1, double n2){
        System.out.println("public double calculate(int n1, double n1)被运行...");
        return n1 + n2;
    }

    public double calculate(double n1, int n2){
        System.out.println("public double calculate(double n1, int n2)被运行...");
        return n1 + n2;
    }

    public int calculate(int n1, int n2, int n3){
        System.out.println("public int calculate(int n1, int n2, int n3)被运行...");
        return n1 + n2 + n3;
    }
}
```

上述程序输出结果如下：

![图2-12 重载程序示例运行结果](images/2024-03-01-21-06-07.png)

##### 细节说明

重载要求：

1. 方法名必须相同
2. 形参列表必须不同。形参**类型**、**个数**或**顺序**，至少有一样不同（仅参数名不同不是重载）
3. 返回类型无要求

> 注意，如果方法名相同，形参类型、个数、顺序也相同，但返回类型不同，也**不构成重载**，此时编译器会认为方法重复定义

#### 作用域

![图2-13 作用域的基本使用](images/2024-03-01-21-30-30.png)

* 全局变量：也就是属性（成员变量），作用域为**整个类体**，该类中的成员方法可以直接使用属性。不赋值也可以直接使用，此时被认定为默认值
* 局部变量：一般是在成员方法中定义的变量，作用域仅**局限于方法内**，并且局部变量**必须赋值后才可以使用**

##### 细节说明

![图2-14 作用域的细节说明1](images/2024-03-01-21-39-17.png)

![图2-15 作用域的细节说明2](images/2024-03-01-21-46-01.png)

全局变量：可以被本类使用，也可以被其他类（通过对象调用的方法）使用。且全局变量可以加修饰符

局部变量：只能在方法类使用且不可以加修饰符

``` Java
public class Main {
    public static void main(String[] args) {
       A a = new A();
       B b = new B();
       b.bTest1();
       b.bTest2(a);
    }

}

class B {
    public void bTest1(){
        A a1 = new A();
        System.out.println("在其他类(B)中使用类A的全局变量age = " + a1.age);
    }
    public void bTest2(A a2){
        System.out.println("通过对象传递在其他类(B)中使用类A的全局变量age = " + a2.age);
    }
}

class A {
    public int age = 15;

    public void aTest(){
        System.out.println("在本类(A)中使用全局变量 age = " + age);
    }
}
```

 上述程序的运行结果：

 ![图2-16 作用域示例程序运行结果](images/2024-03-01-21-57-25.png)

 #### 构造方法/构造器

 构造方法是类的一种特殊方法，其作用是完成对新对象的初始化。构造方法的特点如下：

 * 方法名和类名相同
 * 无返回值
 * 在创建对象时，由**系统自动调用该类的构造方法**完成对象的**初始化**

构造方法示例如下：

```Java
public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("Jack", 50);
        System.out.println("p1的信息如下: ");
        System.out.println("p1的name = " + p1.name);
        System.out.println("p1的age = " + p1.age);
    }

}

class Person {
    String name;
    int age;

    public Person(String pName, int pAge) {
        System.out.println("构造方法被调用....完成对象的初始化！");
        name = pName;
        age = pAge;
    }
}
```

运行结果如下：

![图2-17 构造方法示例程序运行结果](images/2024-03-03-11-36-16.png)

##### 细节

一个类可以定义多个不同的构造器即**构造器重载**

如果程序员没有定义构造器，则**系统会自动生成默认的无参构造器**(默认构造器)，例如 `Person() {}`

但是，一旦定义了构造器，默认构造器就被**覆盖**了，就不能再使用默认的无参构造器（也就是不能再使用 `Person p1 = new Person();`），除非**显示**定义默认构造器