#找规律 #质因数分解 

## 题目大意

有 $n$ 个元素，第 $i$ 个元素的值是 $a_i$。对于任意一对 $(i,j)$ $(1\le i,j\le n)$，你可以选择一个整数 $x$，将 $a_i$ 乘上 $x$，将 $a_j$ 除以 $x$，最后使得所有的元素都是一个值。问你可不可以完成这个操作。

## 思路

首先找规律，我们可以发现将 $a_i$ 分解质因数后，若每一种质因子的数量都是 $n$ 的倍数的话，那么就代表可以化为同一个元素。因为如果是 $n$ 的倍数的话，那么这个质因子就可以互相传递，那么假设数量为 $s$，每一个元素就得到了 $n\div s$，就可以达到判断是否能够达到同一个元素的效果。

现在我们就需要快速分解质因数。假设我们需要分解 $x$，可以考虑分两种情况：

- $x$ 本身就是质数：直接把 $x$ 分离出来；
- $x$ 是合数：枚举 $x$ 的质因子，并直接进行分解。

然后我们使用一个 `map` 存下每一个质因子的数量，最后对 `map` 里面的值进行判断。

## 代码

```cpp
#include <iostream>
#include <map>

using namespace std;

const int kMaxN = 1e4 + 5;

int a[kMaxN], t, n;
map<int, int> f;

int main() {
  for (cin >> t; t; t--) {
    cin >> n, f.clear();
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    for (int i = 1; i <= n; i++) {
      for (int j = 2; j * j <= a[i]; j++) {
        for (; a[i] % j == 0; a[i] /= j) {
          f[j]++;
        }
      }
      if (a[i] != 1) {
        f[a[i]]++;
      }
    }
    bool ans = 1;
    for (auto i : f) {
      ans &= i.second % n == 0;
    }
    cout << (ans ? "YES" : "NO") << '\n';
  }
  return 0;
}
```

