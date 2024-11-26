#几何 #枚举 

## 题目大意

给你 $n$ 个点，现在要你选择其中的三个点组成一个直角三角形，并求出所有可能组成的三角形的面积之和的两倍对 $10^9+7$ 取模后的值。

## 分析

首先，$n\le 10^5$，我们不可能枚举所有的组合。但是，这题明确告诉了我们构造出来的必须是直角三角形，因此肯定有两条边是平行于 $x$ 轴或 $y$ 轴的，而这题值域范围特别小，只有正负 $10^4$，因此我们就可以开多个 [[vector]] 来记录同样的 $x$ 或 $y$ 可以对应哪些不同的 $y$ 或 $x$，然后再枚举平行的点。

但是三重循环还是会超时，我们则需要考虑答案的贡献。对于一个平行于 $x$ 轴的点，与当前点 $y$ 坐标的绝对差值就可以看做三角形的底；另一个平行于 $y$ 轴的点距离当前点 $x$ 坐标的绝对差值，就可以看做不同长度的三角形的高。我们就拿每一个底配所有的高。因此答案就是所有底的长度和乘上所有高的长度和。

**注意：**`long long` 开了没，负数坐标有没有特殊处理，有没有取模？

## 代码

```kotlin
import java.util.*
import kotlin.math.abs

val cin = Scanner(System.`in`)
const val mod = 1e9.toInt() + 7

val n = cin.nextInt()
val x = IntArray(n + 1)
val y = IntArray(n + 1)
val xy = Array(2e4.toInt() + 5) { ArrayList<Int>() }
val yx = Array(2e4.toInt() + 5) { ArrayList<Int>() }

var ans = 0L

fun main() {
  for (i in 1..n) {
    x[i] = cin.nextInt() + 1e4.toInt()
    y[i] = cin.nextInt() + 1e4.toInt()
    xy[x[i]].add(y[i])
    yx[y[i]].add(x[i])
  }
  for (i in 1..n) {
    var s1 = 0L
    var s2 = 0L
    for (j in xy[x[i]]) {
      s1 += abs(y[i] - j)
    }
    for (j in yx[y[i]]) {
      s2 += abs(x[i] - j)
    }
    ans = (ans + s1 * s2) % mod
  }
  println(ans)
}
```