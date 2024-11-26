#二分 #深度优先搜索 

## 题目大意

给定一个 $n$ 个结点的数，现在要你断掉 $k$ 条边，使得所有联通块当中的最小大小最大。

## 思路

最小值最大，而且答案满足单调性，那么我们就可以使用二分求解，然后贪心地对可能的答案进行判断。不难想出，越在下面满足条件的地方进行切分，那么分出的联通块数量也是最大的，最后就看一看是否满足切分了 $k$ 刀即可。

注意一个特判，如果最后一块不够的话就少切一刀。

## 代码

```cpp
#include <iostream>
#include <vector>

using namespace std;

const int kMaxN = 1e5 + 5;

int t, n, m, k, cnt, ans;
vector<int> e[kMaxN];

int dfs(int x, int f) {
  int sum = 1;           // 可用的结点数量
  for (int i : e[x]) {   // 枚举所有儿子
    if (i != f) {
      sum += dfs(i, x);  // 递归并加上儿子可用的结点
    }
  }
  if (sum >= m) {  // 如果可用结点数量够了
    cnt += !f;     // 在不是根结点的情况下断边
    return 0;      // 子树被单独分出来了
  }
  return sum;      // 否则返回可用的结点
}

bool check() {
  cnt = 0;                  // 清零
  int res = dfs(1, 0);      // 根结点的可用数量
  res && res < m && cnt--;  // 不够的话少切一条边
  return cnt >= k;          // 判断是否能够切 k 刀
}

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> k;
    fill(e + 1, e + n + 1, vector<int>());
    for (int i = 1, u, v; i < n; i++) {
      cin >> u >> v;
      e[u].push_back(v);
      e[v].push_back(u);
    }
    for (int l = 1, r = n; l <= r; ) {
      m = (l + r) >> 1;
      if (check()) {
        ans = m, l = m + 1;
      } else {
        r = m - 1;
      }
    }
    cout << ans << '\n';
  }
  return 0;
}
```