#二分 

我们发现答案具有单调性，因为尝试的答案越大满足条件的概率就越高，因此考虑二分。那么，如何判断 $x$ 能不能成为一个正确的答案呢？首先，$a_i-a_{i-1}$ 不能大于 $2x$，因为我们这里只允许添加一个 $d_i+f_j$。然后，不能有两个 $i$ 满足 $a_i-a_{i-1}>x$，原因跟上一个一样。然后就是判断的部分了，如果 $a_i-a_{i-1}$ 不满足条件，那么答案就一定区间 $[a_i-x,a_{i-1}+x]$ 里面，因此我们枚举 $d_i$，然后再二分一个满足条件的 $f_j$ 就行了。注意 $f$ 需要排序。

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

const int kMaxN = 2e5 + 5;

int a[kMaxN], d[kMaxN], f[kMaxN], t, n, m, k, ans;

bool check(int x) {
  int cnt = 0, mn, mx, b = 0;
  for (int i = 2; i <= n; i++) {
    if (a[i] - a[i - 1] > x) {
      mn = a[i] - x;
      mx = a[i - 1] + x;
      b |= a[i] - a[i - 1] > x * 2;
      cnt++;
    }
  }
  if (cnt > 1 || b) {
    return 0;
  } else if (!cnt) {
    return 1;
  }
  for (int i = 1; i <= m; i++) {
    int p = lower_bound(f + 1, f + k + 1, mn - d[i]) - f;
    if (p != k + 1 && d[i] + f[p] >= mn && d[i] + f[p] <= mx) {
      return 1;
    }
  }
  return 0;
}

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> m >> k;
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    for (int i = 1; i <= m; i++) {
      cin >> d[i];
    }
    for (int i = 1; i <= k; i++) {
      cin >> f[i];
    }
    sort(f + 1, f + k + 1);
    for (int l = 0, r = 2e9; l <= r;) {
      int mid = (l + r) >> 1;
      if (check(mid)) {
        ans = mid, r = mid - 1;
      } else {
        l = mid + 1;
      }
    }
    cout << ans << '\n';
  }
  return 0;
}
```