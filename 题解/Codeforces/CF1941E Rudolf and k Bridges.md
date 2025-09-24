#前缀和 #序列dp #单调队列

首先每一行需要花费的成本是不变的，而这里是选择连续的 $k$ 行，因此可以使用前缀和优化。那么我们就需要对每一行求解。

假设当前行的数组为 $a$，那么设 $dp_i$ 表示为修桥修到 $i$ 的成本，这个值就等于所有距离小于等于 $d$ 的 $j$，当中 $dp_j$ 的最小值加上 $a_i+1$。但是这题 $d\le 2\times 10^5$，因此我们需要使用单调队列优化。由于好渴鹅懒得写单调队列，因此直接使用优先队列。

时间复杂度 $\mathcal O(n\times m\log_2 d)$。

```cpp
#include <iostream>
#include <utility>
#include <queue>

using namespace std;
using LL = long long;

const LL kMaxN = 105, kMaxM = 2e5 + 5;

LL a[kMaxN][kMaxM], dp[kMaxM], p[kMaxN], t, n, m, k, d, ans;
priority_queue<pair<LL, LL>, vector<pair<LL, LL>>, greater<>> q;

void solve(LL x) {
  for (; q.size(); q.pop()) { }
  q.emplace(a[x][1] + 1, 1);
  for (LL i = 2; i <= m; i++) {
    for (; q.top().second < i - d - 1; q.pop()) { }
    q.emplace(q.top().first + a[x][i] + 1, i);
  }
  for (; q.top().second != m; q.pop()) { }
  p[x] = q.top().first;
}

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> m >> k >> d;
    ans = 1e18;
    for (LL i = 1; i <= n; i++) {
      for (LL j = 1; j <= m; j++) {
        cin >> a[i][j];
      }
    }
    for (LL i = 1; i <= n; i++) {
      solve(i);
      p[i] += p[i - 1];
    }
    for (LL i = k; i <= n; i++) {
      ans = min(ans, p[i] - p[i - k]);
    }
    cout << ans << '\n';
  }
  return 0;
}
```