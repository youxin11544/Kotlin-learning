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



