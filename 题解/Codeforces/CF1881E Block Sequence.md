#序列dp 

## 题目大意

有 $n$ 个元素，第 $i$ 个元素是 $a_i$。一个合法的块的长度必须是块的第一个元素 $+1$ 的值，而你可以删除若干个元素。问你最少需要删除多少个元素才能使得这 $n$ 个元素可以分成若干个块的组合。

## 思路

看到题目，可能会想到贪心？二分？但是观察样例，如果是贪心的话我们并不能使用一种每次都必定最优的算法，而我们也不能高效地判断一个解是否合法。那么，压力就来到了 dp 这边。

正着操作显然非常麻烦，那么我们就反向操作。我们设 $dp_i$ 表示为把 $i$ 当作第一个块的第一个元素，最少需要更改多少次。那么对于元素 $a_i$，我们可以选择舍去或是保留。舍去就很简单了，直接保留 $dp_{(i+1)}$ 的值并 $+1$；如果保留，那么当前块的长度就是 $a_i$，块后面的第一个元素就是，$dp_{(i+a_i+1)}$。因此状态转移方程就是：
$$
dp_i=\min(dp_{(i+1)}+1,dp_{(i+a_i+1)})
$$

## 代码

```cpp
#include <iostream>

using namespace std;

const int kMaxN = 2e5 + 5;

int a[kMaxN], dp[kMaxN], t, n;

int main() {
  for (cin >> t; t; t--) {
    cin >> n, dp[n + 1] = 0;
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    dp[n] = a[n] != 0;
    for (int i = n - 1; i >= 1; i--) {
      if (i + a[i] <= n) {
        dp[i] = min(dp[i + 1] + 1, dp[i + a[i] + 1]);
      } else {
        dp[i] = dp[i + 1] + 1;
      }
    }
    cout << dp[1] << '\n';
  }
  return 0;
}
```
