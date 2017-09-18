#初识kotlin

#基本语法
1.三个关键字
  - var 声明**可变**的变量
  - val 声明**不可变**的变量
  - fun 声明函数前面需要加上fun关键字，不同于java但是前面的方法修饰 public 这个是和java一样后面会讲到

2.了解编译器推断
  类型转换是自动完成的,无论何时，编译器能够检测没有其它可选项，自动地完成类型转换。
```
 val name = "youxin"
 val name :String = "youxin"
 //上面两个都是对的，因为kotlin会自动推断所以 ：String 可以省略，不过我建议初学着还是加上好点，以后可以去掉
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


