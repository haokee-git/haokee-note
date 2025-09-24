#枚举 

我们发现，计算 $x$ 的所有约数之和非常简单，但是已知约数之和为 $y$，求出最小的 $x$ 非常复杂，答案也不满足单调性。因此，考虑预处理 $1\sim 10^7$ 当中所有数的约数之和。

找到 $x$ 的所有约数是 $\mathcal O(\sqrt x)$ 的，但是这题 $x\le 10^7$。考虑换种方法，不是枚举一个数的因数有哪些，而是枚举一个数的倍数有哪些。准确来说，就是枚举因数 $i$，然后将 $i$ 的所有倍数 $ki$ 的函数值全部的加上 $i$。

这样子时间复杂度大约为 $\mathcal O(n\log_2 n)$，可以极限卡过。

```cpp
#include <iostream>
#pragma GCC optimize(2)

using namespace std;

const int kMaxN = 1e7 + 5;

int f[kMaxN], a[kMaxN], t, x;

int main() {
  ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);
  // 预处理 1 的倍数，常数优化
  fill(f, f + kMaxN, 1);
  // 将所有数的倍数加上这个数
  for (int i = 2; i <= 1e7; i++) {
    for (int j = i; j <= 1e7; j += i) {
      f[j] += i;
    }
  }
  // 记录最小答案
  for (int i = 1; i <= 1e7; i++) {
    if (f[i] <= 1e7 && !a[f[i]]) {
      a[f[i]] = i;
    }
  }
  // 询问
  for (cin >> t; t; t--) {
    cin >> x;
    cout << (a[x] ? a[x] : -1) << '\n';
  }
  return 0;
}
```