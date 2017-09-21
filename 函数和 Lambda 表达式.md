## 函数和 Lambda 表达式
[Lambda 表达式](http://www.yiibai.com/kotlin/lambdas.html)
### 函数的中缀表示法
[中缀表示法](http://www.yiibai.com/kotlin/functions.html)
- 首先说它的使用条件：
  - 他们是成员函数或扩展函数
  - 他们只有一个参数
  - 他们用 infix 关键字标注
- 实际用法：我们先看看几个kotlin的源码


```

 /** Shifts this value left by [bits]. */
    public infix fun shl(bitCount: Int): Int
    /** Shifts this value right by [bits], filling the leftmost bits with copies of the sign bit. */
    public infix fun shr(bitCount: Int): Int
    /** Shifts this value right by [bits], filling the leftmost bits with zeros. */
    public infix fun ushr(bitCount: Int): Int


/**
 * Creates a tuple of type [Pair] from this and [that].
 *
 * This can be useful for creating [Map] literals with less noise, for example:
 * @sample samples.collections.Maps.Instantiation.mapFromPairs
 */
public infix fun <A, B> A.to(that: B): Pair<A, B> = Pair(this, that)


/**
 * Returns a set containing all elements that are contained by both this set and the specified collection.
 * 
 * The returned set preserves the element iteration order of the original collection.
 */
public infix fun <T> Iterable<T>.intersect(other: Iterable<T>): Set<T> {
    val set = this.toMutableSet()
    set.retainAll(other)
    return set
}


/**
 * Returns a progression from this value down to the specified [to] value with the step -1.
 * 
 * The [to] value has to be less than this value.
 */
public infix fun Short.downTo(to: Short): IntProgression {
    return IntProgression.fromClosedRange(this.toInt(), to.toInt(), -1)
}

````

从源码中可以看出 infix 的用法：当我们定义一个类的函数或者扩展函数的时候，如果这个函数接受的参数和自己是同一类的，并且又反回值那么就采用中缀表示法

### 高阶函数与 lambda 表达式
[lambda 表达式](http://www.yiibai.com/kotlin/object-declarations.html)
- 这节内容有的人可能有的学习起来会觉得有点难，其实只要转变一下观点记住下面的几点，就很简单了。看完后就可以愉快的看kotlin源码学习了。
- 一个 lambda 表达式或匿名函数是一个“函数字面值(字面函数)”，即一个未声明的函数，做为表达式传递。
- 函数类型：() -> T
- kotlin 源码大量采用了lambda表达式，这样说明以后自己在写代码的时候，必然也会用到很多，这个也很简单，我们记住这点：将函数用作为参数或返回值的函数是   高阶函数，kotlin一般采用函数字面值(字面函数)的方式往高阶函数传参，一个高阶函数接受另一个lambda 表达式作为**最后一个参数**，lambda 表达式参数可以在
  圆括号参数列表之外传递。
- kotlin的lambda 表达式和高阶函数可以为我们省去以前很多的java接口。下面的接口省掉了OnClickListenter这个接口

```

//简单改造view的setOnClickListenter
class Main2Activity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)
        var view = View()
        view.setOnClickListenter { 
            it->it.toHome()
        }
    }
}
class View{
    fun toHome() {
        
    }
    fun setOnClickListenter(listerner: (v:View) -> Unit) {
        listerner(this);
    }
}

```

```


- 带接收者的函数字面值
