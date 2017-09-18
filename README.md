# Kotlin-Simple
Android开发从java到kotlin

#基本语法
1.三个关键字var val fun


2.了解编译器推断
  类型转换是自动完成的,无论何时，编译器能够检测没有其它可选项，自动地完成类型转换。
```
 val z: View = findViewById(R.id.my_view) 
 if (z is TextView) {
     z.text = "I've been casted!"
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

