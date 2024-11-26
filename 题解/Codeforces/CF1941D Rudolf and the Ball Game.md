#模拟 #序列dp 

我们发现，虽然有可能每一次 $m$ 都是 `?` 的形式，可以产生出 $2^{1000}$ 种状态。但是由于 $n$ 只有 $1000$，而相同位置的状态是可以合并的，因此每一次之后的状态就最多只有 $1000$ 种。设 $dp_{i,j}$ 表示为经过了 $i$ 次操作后能否传到编号为 $j$ 的人，那么这就是一道简简单单的 dp 了。

这里好渴鹅使用了滚动数组的方法，用 $f$ 存储 $dp_{i-1}$，用 $a$ 存储 $dp_i$，然后记得清空。

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

const int kMaxN = 1005;

int f[kMaxN], a[kMaxN], t, n, m, x;
char c;

int forward(int u, int v) { return (u + v - 1) % n + 1; }

int reverse(int u, int v) { return u > v ? u - v : n - (v - u); }

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> m >> x;
    fill(f + 1, f + n + 1, 0), f[x] = 1;
    for (int r; m; m--) {
      cin >> r >> c;
      fill(a + 1, a + n + 1, 0);
      for (int i = 1; i <= n; i++) {
        if (c == '0') {
          a[forward(i, r)] |= f[i];
        } else if (c == '1') {
          a[reverse(i, r)] |= f[i];
        } else {
          a[forward(i, r)] |= f[i];
          a[reverse(i, r)] |= f[i];
        }
      }
      for (int i = 1; i <= n; i++) {
        f[i] = a[i];
      }
    }
    cout << count(a + 1, a + n + 1, 1) << '\n';
    for (int i = 1; i <= n; i++) {
      if (a[i]) {
        cout << i << ' ';
      }
    }
    cout << '\n';
  }
  return 0;
}
```