#质因数分解 #枚举

因为答案肯定在 $[0,2\times 10^6]$ 这个区间里面，因此我们可以考虑枚举所有可能的答案并逐一校验。检验时，我们可以枚举 $i$ 让其他 $j\ne i$ 的 $a_j$ 都改变成 $a_i$。时间复杂度为 $\mathcal O(kn^2)$，但是由于 $k$ 达到了 $2\times 10^6$，因此会超时。

考虑优化校验复杂度。能够发现，当 $a_j>a_i$ 的时候，只需要除可能解的余数一样就行了。因此，我们可以新建一个表用来存余数对应的数量，找到一个数量大于等于 $n/2$ 的余数。时间复杂度为 $\mathcal O(kn)$，仍然超时。

这次，我们不再寻找解了，而是枚举 $a_i$ 找到最优解。对于所有 $a_j>a_i$ 的 $a_j$，都可以通过一个数 $x$ 满足 $(a_j-a_i)\bmod x=0$ 减到 $a_i$，也就是说可能的 $x$ 必须是 $a_j-a_i$ 的因数。因此，我们先求出所有的因数，存进 [[map]] 里面，再找到一个最大的因数 $x$ 满足 $x$ 的数量大于等于 $n/2$ 就行了。时间复杂度 $\mathcal O(n^2\sum\limits_{i=1}^{n}\sqrt{a_i})$。

```cpp
#include <iostream>
#include <unordered_set>
#include <unordered_map>
#include <algorithm>
#include <vector>

using namespace std;

const int kMaxN = 45;

int a[kMaxN], t, n, ans;
vector<int> v;
unordered_map<int, int> f;

unordered_set<int> calc(int x) {
  unordered_set<int> s;
  for (int i = 1; i * i <= x; i++) {
    if (x % i == 0) {
      s.insert(i);
      s.insert(x / i);
    }
  }
  return s;
}

int main() {
  ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);
  for (cin >> t; t; t--) {
    cin >> n;
    ans = -1e9;
    for (int i = 1; i <= n; ++i) {
      cin >> a[i];
    }
    sort(a + 1, a + n + 1);
    // 枚举要变成的
    for (int i = 1; i <= n; i++) {
      // 清空
      int times = 0;
      f.clear();
      v.clear();
      // 枚举其他的数
      for (int j = 1; j <= n; j++) {
        if (a[j] == a[i]) {          // 如果大小一样
          times++;                   // 记录数量
        } else if (a[j] > a[i]) {    // 大于 a[i]
          v.push_back(a[j] - a[i]);  // 加入 vector
        }
      }
      // 如果一样的已经超过了 n/2 就有无数种解
      if (times >= n / 2) {
        ans = 1e9;
        continue;
      }
      // 求因数并记录
      for (int i : v) {
        for (int j : calc(i)) {
          f[j]++;
        }
      }
      // 找最大的答案
      for (auto j : f) {
        if (j.second >= n / 2 - times) {
          ans = max(ans, j.first);
        }
      }
    }
    cout << (ans == 1e9 ? -1 : ans) << '\n';
  }
  return 0;
}
```