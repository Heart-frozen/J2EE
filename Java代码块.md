## Java代码块##

### 一、普通代码块 ###

直接在一个方法中出现的{}就称为普通代码块,例子程序如下: 

```java
public class CodeDemo01{ 

	public static void main(String[] args){ 

		//普通代码块 

        { 

        int x = 10; 	

        System.out.println("x=" + x); 

        } 

		int x = 100; 

		System.out.println("x=" + x); 

	} 

} 

```



### 二、构造代码块 ###

直接在类中定义的没有加static关键字的代码块{}称为构造代码块,例子程序如下: 

```java
public class CodeDemo02{ 

    public CodeDemo02(){ 

    System.out.println("========这是构造方法========="); 

    } 

	//这是构造代码块,而且在new对象时,构造代码块优先构造方法执行 

    { 

    System.out.println("=========这是构造块!========="); 

    } 

    public static void main(String[] args){ 

    new CodeDemo02(); 

    new CodeDemo02(); 

    } 

} 

```



### 三、静态代码块 ###

使用static关键字声明的代码块称为静态代码块,静态块的主要目的是用来为静态属性初始化,例子程序如下: 

```java
public class CodeDemo03 { 

    static{ 

    System.out.println("这是主类中的静态代码块!"); 

    } 

    public static void main(String[] args){ 

    new Demo(); 

    new Demo(); 

    new Demo(); 

    } 

} 

class Demo { 

    static{ 

    System.out.println("这是Demo类中的静态代码块!"); 

    } 

    { 

    System.out.println("这是Demo类中的构造块!"); 

    } 

    public Demo(){ 

    System.out.println("这是构造方法!"); 

    } 

} 

```

静态块优先于主方法的执行,静态块优先于构造方法的执行,而且只执行一次! 

### 四、同步代码块 ###

同步代码块主要出现在多线程中。例如: 

```java
class SellThread implements Runnable{ 

    int ticket = 100; 

    Object obj = new Object(); 

    public void run(){ 

		while(true){ 

			synchronized(obj){ 

				if(ticket > 0){ 

					ticket--; 

				} 

			} 

		} 

	} 

} 

```

