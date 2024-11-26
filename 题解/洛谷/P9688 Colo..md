#序列dp 

## 思路

首先我们看到数据范围：$n\le 500$，因此我们很容易想到序列型 dp。看完题目，可以知道每次选择必定会向后多选一个，这拓扑序不就出来了吗？如果设 $dp_i$ 为状态，很明显，这样是错误的，我们没法知道当前我们已经选择了多少种颜色。怎么办？很简单，加一维状态呗！因此，我们设 $dp_{(i,j)}$ 表示当前选到了第 $i$ 种颜色，其中保留了 $j$ 种颜色所能获得的最大收益。因此，我们可以推出状态转移方程：

$$dp_{(i,j)}=max(dp_{(i,j)},dp_{(l,j - 1)} + b_i)$$

其中，$i$ 表示当前的颜色，$j$ 表示当前已经选择了的颜色数量，$l$ 表示上一个颜色。注意一个细节，选择了一个颜色就必须在序列里加上所有的同颜色格子，因此我们可以直接使用结构体记录每一种颜色的起始位置与终止位置。

## 代码

```cpp
#include <iostream>

using namespace std;
using ll = long long;

const ll kMaxN = 505;

struct Color {  // 每一种颜色
  ll st = 1e9, ed;  // 每一种颜色的起始位置与终止位置
} c[kMaxN];  // n 种颜色
ll a[kMaxN], b[kMaxN], f[kMaxN], dp[kMaxN][kMaxN], n, k, ans = -1e9;

int main() {
  fill(dp[0], dp[0] + kMaxN * kMaxN, -1e9);  // 由于取最大值，所以我们初始化为极小值
  cin >> n >> k;
  for (ll i = 1; i <= n; i++) {
    cin >> a[i], f[a[i]] = 1;  // f[i] 表示 i 颜色是否出现
    c[a[i]].st = min(c[a[i]].st, i);  // 起始位置取min
    c[a[i]].ed = max(c[a[i]].ed, i);  // 终止位置取max
  }
  for (ll i = 1; i <= n; i++) {
    cin >> b[i];
  }
  for (ll i = 1; i <= n; i++) {  // 边界处理
    if (f[i]) {  // 如果当前颜色存在
      dp[i][1] = b[i];  // 当前为第 i 种颜色，选择了 1 种颜色
    }
  }
  for (ll i = 1; i <= n; i++) {  // 枚举当前的颜色
    for (ll j = 2; j <= k; j++) {  // 枚举当前已经选择了 j 个物品
      for (ll l = 1; l < i; l++) {  // 枚举上一种颜色
        if (dp[l][j - 1] != -1e9 && f[i] && f[l] && c[l].ed < c[i].st) {  // 如果状态存在，并且两种颜色也存在，并且当前颜色在后面
          dp[i][j] = max(dp[i][j], dp[l][j - 1] + b[i]);  // 取max进行转移
        }
      }
    }
  }
  for (ll i = 1; i <= n; i++) {  // 枚举最后一种颜色的位置
    ans = max(ans, dp[i][k]);  // 必须全部选完
  }
  cout << (ans == -1e9 ? -1 : ans) << '\n';  // 输出
  return 0;
}
```