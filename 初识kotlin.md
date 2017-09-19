#初识kotlin
（中文可以叫 科特林）

#关于Android studio怎么使用kotlin这点就不用介绍了（网上一大把），需要注意的是Android studio的版本是2.3.3以上
 [kotlin安装方法链接](http://www.cnblogs.com/duduhuo/p/6839990.html)

#基本语法
1.三个关键字
  - var 声明**可变**的变量
- val 声明**不可变**的变量，就想java中final修饰的字符串
 - fun kotlin声明函数前面需要加上fun关键字，不同于java但是前面的方法修饰public 这个是和java一样后面会讲到 

2.了解编译器推断
  类型转换是自动完成的,无论何时，编译器能够检测没有其它可选项，自动地完成类型转换。关于 编译器推断 这个很多文章再讲kotlin都会提到的。
```
 val name = "youxin"
 val name2 :String = "youxin"
 //上面两个都是对的，因为kotlin会自动推断所以 ：String 可以省略，不过我建议初学着还是加上好点，以后可以去掉，编译器在编译name的时候发觉后面给他赋值的是一个字符串，那么编译器就会推断他的类型是String 这就是编译器推断
 val z: View = findViewById(R.id.my_view) 
 if (z is TextView) {
     z.setText ("I've been casted!")
 }
 //这里 z没有经过转型就可以使用
```
 再来看看下面的比较
 ```
 //java
 public String getName(Object object) {
        if (object instanceof String) {
            return (String) object;
        }
        return null;
    }
 
 //kotlin
 fun getName(b:Any):String?{
        if (b is String) {
            return b;
        }
        return null;
    }
 ```
 
#需要改变的观点

1. 在Kotlin中，所有都是对象，没有基本类型，没有void。如果有时没有返回值，实际时返回Unit对象。大多数情况下，Uint可以省略，但是它确实存在的，被隐藏了
  因此，所有这些比哪里都是对象
  
```

  val x: Int = 20
  val y: Double = 21.5
  val z: Unit = Unit
```


2. 和Java一样，Kotlin也是基于JVM的，不同的是，后者是静态类型语言，意味着所有变量和表达式类型在编译时已确定。在Java中，通过装箱和拆箱在基本数据类型    和包装类型之间相互转换，而Kotlin中，所有变量的成员方法和属性都是对象。一些类型是Kotlin中内建，相当于创建的普通类，直接调用即可。
3. 在Kotlin源代码中，不管是常量还是变量在声明是都必须具有类型注释或者初始化。如果在声明时，进行了初始化，会自行推导其数据类型，以为着常量或者变量注    释类型。Kotlin中的数据类型包括数值类型、字符类型、布尔类型等。 
4. 不同于Java的是，字符不属于数值类型。 在Kotlin中，字符类型不是基本数值类型，是一个独立的数据类型。 

5. 在一些kotlin的教程中你会碰到很多穿插**块**这个字的一些文字，比如初始化块，代码块...。块理解成 {} 两个括号之间的代码，就像一整块代码一样。块说的    是代码。一行代码，代码块，初始化块...,这种语句以后自己要习惯。
