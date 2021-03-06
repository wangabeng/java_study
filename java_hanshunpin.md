# lesson 1
### jdk 包含
1 jre  
2 一堆工具包（比如java的编译器 javac.exe java的解释执行器 java.exe）  
3 java的一堆类库 常用的一百五十多个

### 一个java文件只能有一个public的class类

### jvm java虚拟机 就是假的机器 就是虚拟了一个假的机器 java是一个跨平台的 不是在操作系统上运行的 而是在虚拟的机器上运行 ，这个虚拟的机器可以识别java程序。

# lesson 2
### 整数类型 包括
byte 1个字节 -127-128（1个字节等于8个位）
short 2个字节 
int 4个字节
long 8个字节  

byte详解1个字节 8位 第一位是符号位 0表示正 1表示负数 

二进制1这样表示
0 1 1 1 1 1 1 1
- - - - - - - -  
原则上应该是-128  +128 2的7次方
实际上 是  -2的7次方   +2的7次方-1

###java基本数据类型的转换
1 自动转换  
原则1 数据类型可以自动从低精度向高精度转（即低精度交给高精度）。但是反过来 就会报错
int a = 1.2; // 报错 高精度不可以交给低精度  cannot convert from double to int

低精度可以交给高精度 不会出错
double a = 1; // a是1.0

精度高低  
byte<short<int<long<float<double  

思考题：  
```
float a = 3.4; // 编译出错 why  3.4默认是double类型  因为：默认在java中小数是double类型 而double类型不能自动转换成float类型
float a = 3.4f； // 最佳实践 是定义float的时候 数值后面加个f
```

2 强制转换  
高精度转换成低精度  
int a = (int) 1.2; // 1 损失精度

int a = 1;
double b = 3.4;
a = a + b; // 报错a是int型 加3.4 结果会自动往高精度走 是6.4 高精度交给低精度 会报错


# lesson 3
流程控制  

# lesson 4
注意switch  
金字塔练习

# lesson5 
对象和方法

# lesson6
对象和方法

# lesson7 
### 方法声明  
只是声明方法 并没有方法体 不是定义方法 只是声明这里有个方法  
例如  
```
// public 访问修饰符 总共有四种类型
// int 返回值 如果什么都不返回 是void
// abc 函数名
// int a 参数列表
public int abc(int a) {
  // do something
}; 
```

### 构造方法
// 不能有返回值 必须为public
public Person (int age) {
  // do something
}

### 默认构造方法是
pblic Person () {}
但是一旦声明一个构造方法 默认构造方法就被覆盖了。
比如：  
声明了一个构造方法  
```
// 如果在实例化的时候 这样创建 new Person（） 不传值 就会报错 因为默认构造方法被覆盖了 如果想不报错，就必须再创建一个不传值的构造方法 public Person () {}
public Person (int age) {
  this.age = age;
}
```

### 构造方法的主要作用就是初始化成员属性

# lesson8
### this 是属于具体的一个实例化对象的 而不是属于类的

### 有没有一种数据 不属于每个对象 而是属于整个类的？  
这种变量就是静态变量 static变量， 可以通过任何一个具体的实例来访问该静态变量。

# lesson9
### 如何访问类变量 即static变量  
1 类名.变量名  
2 示例对象名.变量名  

### 静态区域块只能被执行一次
![avatar](/img/静态区域块.png)

### 静态区域块什么时候被执行
在定义类的时候 static静态代码块被执行

### 类方法（静态方法）
在java中有个规则 静态变量 原则上 用类方法去访问和操作。static方法中不能访问非static变量，不能放访问成员变量和成员方法。
反过来 普通的成员变量和方法 可以访问静态的变量和静态方法。  

### 类变量小结
![avatar](/img/类变量小结.png)

### java面向对象特征
1 抽象 把类的属性 方法 抽象出来  
2 封装 java中 成员的属性尽可能封装成私有的 方法暴露给外部  
访问控制修饰符  
public（完全公开） 
potected（受保护的 不同包不可以访问 只能在这个包内访问） 也能在子类中访问 
默认（没有修饰符 只能在同类 同包中访问）不能在子类中访问 
private 只能在同类中访问  

# lesson10 访问修饰符 方法覆盖和重写
### 四种访问级别见下图  
![avatar](/img/四种访问级别.png)

### 继承
public属性和方法可以被继承 默认的属性和方法 protected的属性和方法可以被继承。  
如果不希望子类继承某个属性和方法 那么就把它声明为private  

### 继承的注意事项
![avatar](/img/继承的注意事项.png)

### 方法重载(在同一个类中定义 是重载)
如果只是返回类型不一样 不可以构成重载  
如果只是控制修饰符不同 也不可以构成重载

### 方法的覆盖override (又叫方法的重写)  
主要是在继承的子类中 重写父类的方法，而且方法的名称 返回类型 参数是一样的。（并没有说访问修饰符是一样的）  

# lesson11 约瑟夫问题
### 方法覆盖注意事项：  
1 子类的方法的返回类型 参数 方法名称 要和父类方法的返回类型 参数 方法名称完全一致 否则编译出错；  
2 子类方法不能缩小父类方法的访问权限。反过来则可以，即扩大父类方法的访问权限。

### 用链表解决约瑟夫问题 略过

# lesson12 多态
### 多态的实现方式 1 继承 2 接口

### 多态理解 master为 dog喂bone， 为cat喂fish  
![avatar](/img/多态理解.png)

### 多态案例  
```
package abeng.duotai;

public class DuotaiTest {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    /*Cat cat1 = new Cat();
    cat1.cry();
    Dog dog1 = new Dog();
    dog1.cry();*/
    Animal cat1 = new Cat();
    cat1.cry();
    Animal dog1 = new Dog();
    dog1.cry();
  }

}

// 动物类
class Animal {
  private int name;
  public int getName  () {
    return this.name;
  }
  public void cry () {
    System.out.println("不知道怎么叫");
  }
}

// 猫类
class Cat extends Animal {
  public void cry () {
    System.out.println("miaomiao");
  }
}
//狗类
class Dog extends Animal {
  public void cry () {
    System.out.println("wangwang");
  }
}
```

# lesson 13 抽象类

### 什么是抽象类  
当父类的一些方法不能确定时 可以用abstract关键词来修饰该方法【抽象方法】
用abstract来修饰该类【抽象类】
```
// 一个抽象类
// 动物类
abstract class Animal {
  private int name;
  public int getName  () {
    return this.name;
  }
  abstract public void cry (); // 按照java语法规定 在子类中必须实现此抽象方法
}
```

### 抽象类特征
1 抽象类 不可以被实例化 比如这个animal类 就不可以被实例化  
2 抽象类可以不包含abstract方法
3 一旦包含了abstract方法 此类必须声明为抽象类  
4 抽象方法不能有主体

### 接口
接口中的变量 必须是static 而且是final的 即便不写前缀 也是 而且不能被更改
```
interface Usb {
  int a = 2; // 默认是static final的 不能被更改的 不能用private修饰 而且必须被初始化赋值
}
```
小技巧 很多程序员喜欢用接口来定义全局变量

### final
![avatar](/img/final.png)

# lesson14 点评

# lesson15 点评

# lesson16 数组

### 数组定义
int[] abc = new int[5]; // 定义一个长度为5的 存放int类型的数组

#lesson17 排序
### 交换排序
交换排序1 冒泡排序bubble sort
交换排序2 快速排序quick sort

# lesson 18 查找

# lesson 19 多为数组

# lesson 20 位运算

# lesson 21 集合

# lesson 22 集合 ArrayList

# lesson 23 集合 HashMap HashTab 

## 韩顺平很喜欢HashMap HashTable 都是键值对

## ArrayList Vector区别同 HashMap 与 HashTab的区别类似。 
1 Vector同步的，线程安全   
ArrayList异步的，不安全。  
2  数据增长  
Vector数据自动增长为原来的1倍(适用于大量的数据)    
ArrayList数据自动增长为原来的0.5倍  

# lesson 24 集合总结
![avatar](/img/集合选择建议.png)

# lesson 25 泛型 异常 
## 泛型基本概念  
![avatar](/img/泛型基本概念.png)

## 泛型demo  
1 src下新建包 定义泛型工具类 abeng.test.cn 新建 Tool.java；  
```
package abeng.test.cn;

// 泛型可以理解为定义一个未知的类型
public class Tool<E> {
  public E abc;
  // 构造函数必须为public
  public Tool (E edd) {
    this.abc = edd;
  }
}
```
2 src下新建包 使用泛型类 abeng.test.com 新建UseTool.java;
```
package abeng.test.com;

import abeng.test.cn.*;

public class UseTool {
  public static void main (String[] args) {
    // Volume<Circle> c1v=new Volume<Circle>(c1,2.5) 使用泛型类
    Tool<String> a = new Tool<String>("abeng");
    System.out.println(a.abc);
  }
}
```
## 泛型反射机制
```
package abeng.fanxing;

public class Fanxing {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    Gen<String> genObj = new Gen<String>("aaaa");
    genObj.showTyppeName();
  }

}

class Gen<E> {
  private E abc;
  public Gen (E a) {
    this.abc = a;
  }
  public void showTyppeName () {
    System.out.println(abc.getClass().getName()); // 'java.lang.String'  体现反射机制  通过反射机制可以得到Gen的很多信息 
  }
}

```
## 异常处理
java中2种方法处理异常：  
1 在发生异常的地方直接处理；
2 将异常抛给调用者，让调用者处理。

## 异常分类
1 检查性异常  
程序正确，但是因为外在的环境条件不满足引发。例如：用户错误及I/O问题——程序试图打开一个并不存在的远程Socket端口，或则打开一个不存在的文件。这不是程序本身的逻辑错误，而很可能是远程机器名字错误(用户拼写错误)。必须捕获这类异常，否则程序将不能被编译。  
```
package abeng.zhengchu;
import java.io.*;

public class ExceptionTest {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    FileReader abc = new FileReader("d:/d.txt");
  }

}
```
2 运行期异常  
程序存在bug，如数组越界，0被除，入参不满足规范---这类异常需要更改程序来避免。java编译器强制要求处理这类异常。
```
package abeng.zhengchu;
import java.io.*;

public class ExceptionTest {

  public static void main(String[] args) {
    int a = 4 / 0; 
    
  }

}
```
3 错误  
一般很少见，也很难通过程序来解决。他可能源于程序的bug，但一般更可能源于环境问题，如内存耗尽。错误在程序中无须处理，而由运行环境处理。

# lesson 26 常处理
## 代码自动补全（提示）alt + /
1 处理异常  
```
package abeng.zhengchu;
import java.io.*;

public class ExceptionTest {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    try {
      int a = 4 / 0;
    } catch (Exception e) {
      // TODO: handle exception
      e.printStackTrace(); // java.lang.ArithmeticException: / by zero
                            // at abeng.zhengchu.ExceptionTest.main(ExceptionTest.java:9)
    }
  }

}
```
以上方法是最大捕获异常，还有人推荐会出现什么异常，就捕获什么异常。（即最小捕获）
2 最小捕获。在异常语句的错误提示上选择suronded width try/catch即可
```
package abeng.zhengchu;
import java.io.*;

public class ExceptionTest {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    try {
      FileReader abc = new FileReader("d:/d.txt");
    } catch (FileNotFoundException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }

}

```
3 抛出异常交给调用者处理
```
public void test () throw Exception { // 抛出异常
  
}
// 调用的时候try catch 用法同上 略
```

# lesson 27 作业点评

# lesson 28 面试评讲

# lesson 29--52 GUI swing编程 略（其中的线程和IO编程需要单独学习）

# lesson 38 线程的理解
![avatar](/img/线程理解.png)
一个简单的线程demo
```
package abeng.zhengchu;

public class ThreadTest {
  public static void main(String[] args) {
    Cat newCat = new Cat();
    newCat.start();
    
  }
}

class Cat extends Thread {
  // 重写run函数
  public void run () {
    System.out.print("ddd");
  }
}
```

## 一个需求 每隔100毫秒 cat叫一次
用线程的sleep方法 sleep会使线程进入阻塞状态，并释放此线程占用的资源  
```
Thread.sleep(100);  // 休眠100毫秒
```
## 线程的5个状态
![avatar](/img/线程状态图.png)

## 通过runable接口的方式来实现线程(推荐实现接口的方法实现线程)
为什么要使用这个runnable？ 
因为java是单继承的，如果一个类已经继承了一个类，就不能再继承thread类了，所以可以通过实现runable接口来创建线程。
需求 通过继承runnable方式实现每隔一秒打印一次hello world
```
package abeng.zhengchu;

public class ThreadTest2 {

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    Dog dog = new Dog();
    Thread t = new Thread(dog);
    t.start();
  }

}

class Dog implements Runnable {
  int times = 0;
  public void run () {
    while (true) {
      try {
        Thread.sleep(1000);
      } catch (Exception e) {
        e.printStackTrace();
      }
      times ++;
      System.out.print("Hello world");
      if (times == 10) {
        break;
      }
    }
  }
}
```
# lesson 39 多线程
两种线程用法的区别
![avatar](/img/线程区别.png)

# lesson 43 IO编程
1 文件流的基本概念  
![avatar](/img/文件流概念.png)  
2 如何判断是输入流还是输出流？  
以内存为参照。如果向内存流动，就是输入流。反之，就是输出流。  
3 文件流分类  
![avatar](/img/文件流分类.png)

# lesson 44 45 IO编程（3个案例）
# lesson 84 网络编程

-----------------------
# lesson 53-67 数据库相关
