#模拟

首先，我们将相同的 $c_i$ 存到同一个 [[vector]] 里面，然后处理所有的更改。更改分为必选更改和可选更改（$a_i\ne b_i$ 为判定条件）。对于必选更改，我们要在 $b_i$ 对应的 vector 里面找到随便一个元素（一般是最后一个）并删除；对于可选更改，我们只需要找到那个元素就行了。

为什么要找到那个元素呢？因为假如那个元素是第 $j$ 个更改，所有的 $j$ 当中的最大值也就是可以应用到 $a$ 数组当中的最后一个更改。如果这就是 $m$ 个更改当中的最后一个，那么就有解，否则无解。时间复杂度 $\mathcal O((n+m)\log_2 m)$。

```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <map>
#include <set>

using namespace std;

const int kMaxN = 2e5 + 5;

int a[kMaxN], b[kMaxN], t, n, m, ch, ans;
map<int, vector<int>> f;
set<int> s;

int main() {
  ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);
  for (cin >> t; t; t--) {
    cin >> n, ans = 0, ch = 1;
    s.clear(), f.clear();
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    for (int i = 1; i <= n; i++) {
      cin >> b[i];
    }
    cin >> m;
    for (int i = 1, x; i <= m; i++) {
      cin >> x;
      f[x].push_back(i);
    }
    for (int i = 1; i <= n; i++) {
      if (a[i] == b[i]) {
        if (f.count(b[i])) {
          ans = max(ans, f[b[i]].back());
        }
        continue;
      }
      if (f.count(b[i])) {
        ans = max(ans, f[b[i]].back());
        f[b[i]].pop_back();
        if (f[b[i]].empty()) {
          f.erase(b[i]);
        }
      } else {
        ch = 0;
      }
    }
    cout << (ans == m && ch ? "YES" : "NO") << '\n';
  }
  return 0;
}
```