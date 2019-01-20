# 用git的时候出的问题
```
cd C:\Program Files\Java\jdk1.8.0_172\bin
报错
Git: bash: cd: too many arguments
原因 
路径中间有空格 需要用引号包起来
解决方法
cd 'C:\Program Files\Java\jdk1.8.0_172\bin'
```

# java的安装
1 先要有运行java的环境  
方法1.1 安装java运行环境方法一（不推荐 不能手动编译 只能通过编译软件eclipse编译） 
首先安装jre，可以去官方下载。注意win7 32位对应的版本。
安装jre到
```
D:\Program\Java\jre1.8.0_162
```  
此时在命令行 java 会输出命令提示，但是如果输入javac 则提示不是内部命令。就是说java的运行环境已经生成，只是同javac不能编译，如果安装eclipse就可以用eclipse来编译。

方法1-2
    1 安装jdk（下载jdk安装后 也就自带了jre 安装jdk后会自动安装jre，需要注意的是 安装的时候不要安装在一个文件夹里）jdk安装在D:\Program\Java\jdk1.8.0，而jre安装在 D:\Program\Java\jdk1.8.0。   
    2 配置环境变量。打开环境变量窗口，在‘系统变量’-‘新建’-变量名输入：JAVA_HOME 变量值输入 D:\Program\Java\jdk1.8.0  
    3 在‘系统变量’中找到‘path’，双击编辑，在尾部添加    ;%JAVA_HOME%\bin  
    4 然后保存。在命令行中输入javac 如果出现帮助命令，则表示安装成功。


2 安装eclipse 
直接安装在 d:/java-oxygen。安装完成后打开eclipse 会让选择工作目录。
选择D:\javaworkspace

3 成功

# 开始一个新的java项目
1 打开eclipse file-new java project然后项目名称命名 hello。然后会在工作目录生成一个hello文件夹 文件夹下有几个初始化的文件
D:\javaworkspace\hello
2 在eclipse的hello项目，找到/src目录 然后鼠标右键 new-class 然后弹出一个对话框。然后给class命名Hello，注意首字母大写。
然后勾选public void main,然后确定。此时会在src下创建一个hello文件夹，生成一个
Hello.java文件。
```
package hello;


public class Hello {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// 输入
		System.out.println("Hello world!");
	}

}
```
技巧： alt+/ 自动命令提示.
输入
```
System.out.println("Hello world!");
```
3 运行程序 点击播放按钮 会输出"Hello world!"

# 运行javac的时候出错 Picked up _JAVA_OPTIONS: -Xmx512M
可能的原因 在安装cordova的时候增加了一个环境变量  
_JAVA_OPTIONS  = -Xmx512M
解决办法  
暂时先删除此环境变量 需要的时候再装  

# 产生随机数
用 Math.randomO 来获得一个 0.0 到 1.0 之间的随机 double 值，不包括 1.0

# java中的单引号
不要在java中 使用单引号 切记

# public static viod main 主函数是不带返回值的 
public static int main 所以类似这样的写法就是错误的

# java的一个冒泡排序
```
public class Sortvalue {
  static int[] lists = {3, 1, 5, 6};

  public static void main (String []args) {
    for (int i = 0; i < lists.length - 1; i++) {
      // 比较 是否交换位置
      for (int j = i + 1; j < lists.length; j++) {
        if (lists[i] < lists[j]) {
          int middleValue = lists[i];
          lists[i] = lists[j];
          lists[j] = middleValue;
        }
      }
    }

    for (int j = 0; j < lists.length; j++) {
      System.out.println(lists[j]);
    }
    
  }
}
```

# 比较对象的相等 比如String对象 不能用 == 判断 而用StringA.equals(StringB) true是相等 false是不等

# 参数错误抛出异常
```
if(n<0) {
	throw new IllegalArgumentException("错误是：" + n); // so so
}
```
一旦抛出异常，thorw之后的代码就不会执行了

# 数值类型的转换
总是可以将一个数值陚给支持更大数值范围类型的变量，例如，可以将 long 型的值陚给 float 型变量。但是，如果不进行类型转换，就不能将一个值賦给范围较小类型的变量。  
Java 将自动拓宽一个类型，但是，缩窄类型必须显式完成。将一个小范围类型的变量转换为大范围类型的变量称为拓宽类型（ widening a type ), 把大范围类型的变量转换为小范围类型的变量称为缩窄类型（ narrowing a type)。
比如  
```
int a = 123;
double b = a; // 123.0 可以将一个数值陚给支持更大数值范围类型的变量
// int c = b;  // 此时就无法编译 必须把发范围的类型强制转换为小范围的
int c = (int)b; // 123 强制转换后就不会报错

```
# 超出预期的整数除法
当两个操作数是整数时，/ 操作符执行一个整数除法，操作的结果是整数，小数部分被截去。要强制两个整数执行一个浮点数除法时，将其中一个整数转换为浮点数值。

# 比较两个浮点数是否相等
不能直接比较 
```
double x = 1.0 - 0.1 - 0.1 - 0.1 - 0.1 - 0.1;
System.out.println(x == 0. S); // 本来应该是true的 但是确是false
// 正确的比较方法
final double EPSILON = IE-14;
double x = 1.0 - 0.1 - 0.1 - 0.1 - 0.1 - 0.1;
if (Math.abs(x - 0. S) < EPSILON)
System.out.printlnCx + " is approximately 0.5")；// 将显示 0.S000000000000001近似等于 0.5

```

# 理解异或 a^b 等价于a!=b 只有a和b不相等 才成立
如果a为true b为true 则表达式为false ；如果a为false b为false 则表达式为false；如果a为true b为false 则表达式为true；

# Java中一元加号和二元加法有什么区别
一元运算符有且只有一个运算参数  
二元运算符有且只有两个运算参数  
例如 负号 - 1 ; 它只能运算一个数据  
加号 1+ 2 ；参加运算的只能是两个数据多或者少都出错 它是二元运算符  

# java中操作符优先级
最高到最低 递减
```
最高级 var++ 或 var--(后置操作符)
	+ - （一元加 一元减） ++var --var （前置操作符）
	(type)value (类型转换)
	! (非)
	*、/、％(乘法、除法和求余运算）
	+、- (二元加法和减法）
	<、<=、>、>= (比较操作符）
	=、!=(相等操作符）
	^ (异或）
	&&(条件与）
	|| (条件或）

最低级   =、+= 、-=、*=、/=、％=(陚值搡作符）

```

# 入坑记 java静态方法不可以调用非静态方法和成员 例如
```
package how2j;

public class Hero {
	boolean b = true;
	static double abc = 12.0;
	
	public static void main(String[] args) {
		if (b) {
			System.out.println(b);
			System.out.println(abc);
		}
	}


}
```
运行时报错： Cannot make a static reference to the non-static field b  
解决办法：boolean b = true; 改为 static boolean b = true;

# 泛型
```
//  泛型：就是一种不确定的数据类型。
// 比如：ArrayList<E> E就是泛型。 这种不确定的数据类型需要在使用这个类的时候才能够确定出来。
// 泛型可以省略，如果省略，默认泛型是Object类型。
// 泛型的好处：
//   1. 省略了强转的代码。
//   2. 可以把运行时的问题提前到编译时期。
public class Demo01Generic {
    public static void main(String[] args) {


        //创建集合不给出泛型
        ArrayList list = new ArrayList();
        list.add("hello");
        list.add("java");
        list.add("world");
        //遍历集合
        for (Object obj : list) System.out.println(obj);
//进行遍历，打印出每个字符串长度
        for (Object obj : list) {
            String str = (String) obj;/*此处练习了向下转型*/
            System.out.println(str.length());
        }
        //创建集合给出泛型
        ArrayList<String> list2 = new ArrayList<>();
        //添加元素
        list2.add("helloo");
        list2.add("helo");
        list2.add("world");
         //list2.add(100);编译的时候就会报错，如果没有给出泛型，则不会报错
        //使用增强for遍历集合
        for (String str2 : list2
                ) {
            System.out.println(str2);

        }
    }

}

```
# 引包调用类出现问题 The constructor Indivi() is not visible 
原因 构造函数未设置public属性

# 泛型demo
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

# java hashMap存储键值对集合
```

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;
 
public class Demo3_Iterator {
 
  public static void main(String[] args) {
    Map<String, Integer> map=new HashMap<>();
    map.put("张三", 23);
    map.put("李四", 24);
    map.put("王五", 25);
    map.put("赵六", 26);
////    Map.Entry说明Entry是Map的内部接口，将键和值封装成了Entry对象，并存储在set集合中
//    Set<Map.Entry<String,Integer>>  entery=map.entrySet();
////    获取每一个对象
//    Iterator<Map.Entry<String,Integer>> it=entery.iterator();
//    while(it.hasNext()) {
////      获取每一个Entry对象
//      Map.Entry<String, Integer> en=it.next();
//      String key=en.getKey();//根据键值对对象获取键
//      Integer Value=en.getValue();//根据键值对对象获取值
//      System.out.println(key+"="+Value);
//    }
    for(Map.Entry<String,Integer> en:map.entrySet()) {
      System.out.println(en.getKey()+"="+en.getValue());
    }
  }
 
}
```
# hashMap迭代方式(效率最高):
需要导入包 Map HashMap Iterator  
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;  
```
Map map = new HashMap();
Iterator iter = map.entrySet().iterator();
while (iter.hasNext()) {
	Map.Entry entry = (Map.Entry) iter.next();
	Object key = entry.getKey();
	Object val = entry.getValue();
}
```
一个实例
```
package abeng.test.com;

// import abeng.test.cn.*;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

public class UseTool {
	public static void main (String[] args) {
		Map map = new HashMap();
	    map.put("张三", 23);
	    map.put("李四", 24);
	    map.put("王五", 25);
	    map.put("赵六", 26);
	    
		Iterator iter = map.entrySet().iterator();
		while (iter.hasNext()) {
			Map.Entry entry = (Map.Entry) iter.next();
			Object key = entry.getKey();
			Object value = entry.getValue();
			System.out.println(key + " and " + value);
		}
	}
}
```

# eclipse历史版本下载
https://wiki.eclipse.org/Older_Versions_Of_Eclipse

----------
# servlet中cookie的使用
cookie的目的：每次发送请求的时候 每次都有同样的数据，比如每次都有用户名，可不可以第一次发送请求的时候，服务器把这个用户名保存起来，返回给浏览器，浏览器下次即便不请求同样的地址，只要是请求这个web项目，发送的数据即便不定义，也会自动带有这个用户名信息。这就是cookie技术。  

## cookie使用原理：  
1 浏览器发送请求，带有用户名信息；  
2 服务器返回response 把用户名信息保存到cookie中，返回给浏览器；  
```
 Cookie c = new Cookie("mouse", "thinkpad");
 response.addCookie(c);
```
注意： 一个Cookie对象只能存储一条Cookie数据，如果想存储多条数据，只有多创建cookie对象。  
3 浏览器下次发送请求，（无论发送到哪个页面的请求，只要是这个web工程）都将自动带这个用户名的信息  

## cookie的特点(创建和存储)：  
1 是一种浏览器端的数据存储技术。声明和设置在服务器中，使用是在浏览器中使用。  
2 一旦把浏览器关闭，再次打开的时候，cookie就丢失了。说明cookie实际上存储在客户端的运行内存中。
3 cookie的存储方式有两种，临时存储和定时存储。临时存储存储在浏览器的运行内存中，浏览器关闭则cookie失效；  
定时存储，可以设置cookie的有效期，设置了有效期的cookie存储在客户端的硬盘中。
```
  // 设置cookie 定时存储
     Cookie c2 = new Cookie("benname", "wangbenben");
     c2.setMaxAge(1000 * 60);
     response.addCookie(c2);
```

4 设置好cookie之后，每次请求web工程页面，都会自动附带cookie数据，除非设置存储路径。  
设置cookie的请求路径，比如/data，那么只有输入/data的请求，才会带这个cookie的请求数据。
```
     Cookie c2 = new Cookie("benname", "wangbenben");
     c2.setMaxAge(1000 * 60); // 设置有效期
     c2.setPath("/date");
     response.addCookie(c2);
```

## cookie的使用：
在服务器端servlet中cookie的获取  
在request中获取
```
Cookie[] cks = req.getCookies();
if (cks != null) { // 防止出现空指针异常
  for (Cookie c:cks) {
    // 获取键值对
    String name = c.getName(); 
    String value = c.getValue();
  }  
}

```
重点： 重启服务器，cookie不会失效，为什么？因为cookie存储到浏览器端了。

## cookie实际使用案例 三天免登录
实现原理：  
判断请求中是否携带正确的cookie信息  
如果有 则校验cookie信息是否正确  
  如果正确 则直接相应主页面给用户  
  如果校验不正确 则响应登录页面给用户 
没有cookie信息 则请求转发给登录页面  
  
在登录页面 如果用户登录成功 保存用户的uid在cookie中 并设置cookie的有效期 为3天 
且设置cookie路径为特定路径的时候才带这个cookie


# session技术
  



