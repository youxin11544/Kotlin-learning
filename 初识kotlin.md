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

1.在Kotlin中，所有都是对象，没有基本类型，没有void。如果有时没有返回值，实际时返回Unit对象。大多数情况下，Uint可以省略，但是它确实存在的，被隐藏了
  因此，所有这些比哪里都是对象：
  
```
  val x: Int = 20
  val y: Double = 21.5
  val z: Unit = Unit
```

