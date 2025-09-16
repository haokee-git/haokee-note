#贪心

首先，看到 $1\le a_i\le 10^9$，我们暴力出奇迹的念头就已经消失了。但是我们能够发现，让乘积为 $2^n$ 的倍数就等同于所有数当中 $2$ 的因子的数量需要大于等于 $n$，而一个数 $2$ 的因子的数量很容易计算，因此我们就能很轻易地判断不执行任何操作能否满足条件。

然后就是贪心地去操作了。要想让在尽可能少的操作数量下 $2$ 的因子的数量尽可能的多，那么乘上的 $i$ 的 $2$ 的因子数量也要尽可能的多，因此我们只需要预处理出 $1\sim n$ 所有数的因子数量，然后从大到小排一个序，最后再贪心地选择即可。

```kotlin
import java.util.*

val cin = Scanner(System.`in`)

fun main() {
  for (t in 1..cin.nextInt()) {  // t 组数据
    val n = cin.nextInt()        // 元素数量
    var cnt = 0                  // 记录因子数量
    var ans = 0                  // 记录答案
    val a = IntArray(n + 1)      // 1—n 的因子数
    for (i in 1..n) {
      var x = cin.nextInt()
      while (x % 2 == 0) {       // 如果还有 2 的因子
        cnt++                    // 记录数量
        x /= 2                   // 去掉
      }
    }
    for (i in 1..n) {            // 预处理 1—n 的因子数
      var x = i
      while (x % 2 == 0) {       // 如果还有 2 的因子
        a[i - 1]++               // 记录数量
        x /= 2                   // 去掉
      }
    }
    a.sortDescending()           // 从大到小排序
    for (i in 0..<n) {           // 遍历前 n 个元素
      if (cnt >= n) {            // 已经满足要求
        break                    // 跳出循环
      }
      cnt += a[i]                // 计数器累加
      ans++                      // 记录答案
    }
    println(if (cnt >= n) ans else -1)
  }
}
```