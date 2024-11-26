#贪心

## 题目大意

给定一个长度为 $n$ 的数组 $a$，你需要进行 $k$ 次操作，每一次操作都可以选择一个连续的子序列（可以为空），然后将这个子序列的和作为一个元素插入到这个数组当中。问你最后数组的和最大能够是多少，对 $10^9+7$ 取模。

## 思路

首先，题目告诉了我们这题是「最大值取模」而不是「取模后的最大值」，因此我们可以考虑贪心。我们可以先找到最大字段和，然后把它的和插入到旁边这个操作等同于对最大字段和的值 $\times 2$，而不会新加入其他的元素。因此，我们直接模拟就可以了。

## 代码

```cpp
#include <iostream>

using namespace std;
using LL = long long;

const LL kMaxN = 2e5 + 5, kMod = 1e9 + 7;

LL a[kMaxN], dp[kMaxN], t, n, k, mx, ans;

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> k, ans = mx = 0;
    for (LL i = 1; i <= n; i++) {
      cin >> a[i];
    }
    for (LL i = 1; i <= n; i++) {  // 求最大字段和
      mx = max(mx, dp[i] = max(dp[i - 1] + a[i], a[i]));
    }
    ans = -mx;  // 注意 ans 需要额外减去原来的部分
    for (; k--; mx = mx * 2 % kMod) { }  // 增长 n 次
    for (LL i = 1; i <= n; i++) {
      ans = (ans + a[i] + kMod) % kMod;  // 求数组和
    }
    cout << (ans + mx + kMod) % kMod << '\n';  // 加起来
  }
  return 0;
}
```