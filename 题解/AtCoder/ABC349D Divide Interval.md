#贪心

贪心。先说结论：对于当前左边界 $l$，想要尽可能快地靠近 $r$，那么我们需要找到一个最大的 $p$ 使得 $l\bmod 2^p=0$ 且 $l+2^p\le r$，然后将 $l$ 加上 $2^p$ 即可，不断重复操作。

为什么能这样子呢？考虑如下二进制 $100110$，满足 $l\bmod 2^p=0$ 的 $p$ 有 $0$ 和 $1$（$2^p$ 分别为 $1$ 和 $2$），其实第一个 $1$ 及后面的位置。由于我们可以加上 $2^p$，那么就可以将那个位置加上 $1$，然后进位。能够发现，每次都加在前面的一定不会更劣。因为如果我们先加后面在加前面的话，万一位置过于靠后，那么就需要一位一位加起来；而先加上前面的在加后面的每次先把尽可能大的给加了，那么后面的小的就不会多加。

可能比较抽象，代码可能会要直观一点。

```kotlin
import java.util.*

val cin = Scanner(System.`in`)

var l = cin.nextLong()
val r = cin.nextLong()
val ans = ArrayList<Pair<Long, Long>>()  // 记录答案

fun main() {
  while (l < r) {                  // 一直循环直到 l == r
    val t = l                      // 保存 l 之前的值
    var p = 0                      // 思路中有详解
    for (i in 0..60) {             // 不断循环
      if (l + (1L shl i) > r) {    // 如果已经超出了 r
        break;                     // 直接退出循环
      }
      if (l % (1L shl i) == 0L) {  // 如果能够整除
        p = i                      // 记录下来
      }
    }
    l += 1L shl p                  // 更新 l
    ans.add(Pair(t, l))            // 加入答案数组
  }
  // 打印答案
  println(ans.size)
  for (i in ans) {
    println("${i.first} ${i.second}")
  }
}
```