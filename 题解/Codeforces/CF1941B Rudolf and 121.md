#贪心

首先，我们发现想要将 $a_i$ 变成 $0$ 有三种办法，但是如果 $a_{i-1}$ 已经等于 $0$ 的话，那么就只能使用 $a_{i}-1,a_{i+1}-2$ 的方法。所以我们就枚举中间的数，如果 $a_i$ 大于零那么就将 $a_{i+1}$ 进行若干次操作，直到 $a_i$ 等于零。最后我们检查一遍，只要有不为 $0$ 的就是无解。时间复杂度 $\mathcal O(\sum n)$。

```cpp
#include <iostream>

using namespace std;

const int kMaxN = 2e5 + 5;

int a[kMaxN], t, n, ans;

int main() {
  for (cin >> t; t; t--) {
    cin >> n, ans = 1;
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    for (int i = 1; i <= n - 2; i++) {
      if (a[i] > 0) {
        a[i + 1] -= a[i] * 2, a[i + 2] -= a[i], a[i] = 0;
      }
    }
    for (int i = 1; i <= n; i++) {
      ans &= !a[i];
    }
    cout << (ans ? "Yes" : "No") << '\n';
  }
  return 0;
}
```