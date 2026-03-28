## 题目描述

给定 $N$ 对数 $(T_i,P_i)$，现删去 $D$ $(1\le D<N)$ 对数。问有多少个满足条件的 $D$，使得存在另外一种删除 $D$ 对的方式，使得剩余 $\cfrac{\sum T}{\sum P}$ 比删除 $\cfrac{T_i}{P_i}$ 最小的 $D$ 对 剩下的$\cfrac{\sum T}{\sum P}$ 更大。

## 题解

首先，如果有另外一种删除方式使得 $\cfrac{\sum T}{\sum P}$ 比删除 $\cfrac{T_i}{P_i}$ 最小的 $D$ 对更大，那么一定存在：在 $\cfrac{T_i}{P_i}$ 最小的 $D$ 对当中，抽出一个保留；再删除一个 $\cfrac{T_i}{P_i}$ 较大的，剩下的 $\cfrac{\sum T}{\sum P}$ 更大。

证明：把它们保留的共同元素提出来不管。对于剩下保留的不同元素，在更优方案中一定有一个保留价值比原先保留方案的其中一个大的元素；否则新方案不会比原先的方案大。

考虑用函数来描述“保留价值”。设目前答案值为 $r=\cfrac{\sum T}{\sum P}$，那么将第 $i$ 个元素的保留价值表示为 $w_i=T_i-r\cdot P_i$。显然：$w_i>0$ 则保留 $i$ 有正收益，$w_i<0$ 则保留 $i$ 有负收益；若 $w_i<w_j$，则保留 $j$ 比保留 $i$ 更有价值。

既然我们保留前 $k=n-D$ 个，那么若 $(k,n]$ 当中有一个元素 $j$ 保留价值比 $[1,k]$ 其中一个元素保留价值 $i$ 更高，则保留 $j$ 删除 $i$ 比原先的删除 $j$ 保留 $i$ 的最终值更大。

即
$$
\begin{aligned}
&\textcolor{transparent}{\Leftrightarrow}\min_{i=1}^k w_i<\max_{i=k+1}^n w_i \\
&\Leftrightarrow\min_{i=1}^k\left(T_i-r\cdot P_i\right)<\max_{i=k+1}^n\left(T_i-r\cdot P_i\right)\\
&\Leftrightarrow\min_{i=1}^k\left(T_i-\cfrac{\sum T}{\sum P}\cdot P_i\right)<\max_{i=k+1}^n\left(T_i-\cfrac{\sum T}{\sum P}\cdot P_i\right)\\
&\Leftrightarrow\min_{i=1}^k\left(\sum P\cdot T_i-\sum T\cdot P_i\right)<\max_{i=k+1}^n\left(\sum P\cdot T_i-\sum T\cdot P_i\right)
\end{aligned}
$$
则此时 $D$ 满足条件。注意此处的 $\sum P$ 和 $\sum T$ 是剩余的前 $k$ 项的和。

考虑快速求 $f_k=\min\limits_{i=1}^k\left(\sum P\cdot T_i-\sum T\cdot P_i\right)$ 和 $g_k=\max\limits_{i=k+1}^n\left(\sum P\cdot T_i-\sum T\cdot P_i\right)$。

先返回原来的 $w_i=T_i-r\cdot P_i$。比较两决策点 $j<j'$，$j'$ 比 $j$ 不劣当且仅当 $r_k\le\cfrac{T_j-T_{j'}}{P_j-P_{j'}}$。由于 $r_k=\cfrac{\sum T}{\sum P}$ 随着 $k$ 的增大而减小（不断加入比值更小的分数），$j'$ 始终不劣于 $j$。因此，$f_k$ 实际取到最小值的 $i$ 随着 $k$ 的增大而增大。

同理，$g_k$ 实际取到最大值的 $i$ 也随着 $k$ 的增大而增大。

因此，决策点 $i$ 总是单调递增。考虑决策单调性分治。以求 $f_k$ 为例：

- 令 $\text{solve}(l,r,s,t)$ 为求 $k\in[l,r]$ 的 $f_k$，其中最优决策点 $i\in[s,t]$。
- 为 $f_m$ $\left(m=\left\lfloor\cfrac{l+r}{2}\right\rfloor\right)$ 暴力在 $[s,t]$ 中找出最优的 $i$。注意 $i$ 不能大于 $m$（由。
- 左边的 $[l,m)$ 最优决策点位置一定小于等于 $i$，右侧的一定大于等于 $i$。
- 递归计算 $\text{solve}(l,m,s,i)$ 和 $\text{solve}(m+1,r,i,t)$。

$g_k$ 的计算同理。

时间复杂度 $\mathcal O(n\log n)$。

```cpp
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;
using LL = long long;

const LL kMaxN = 5e4 + 5;

struct {
  LL t, p;
} a[kMaxN];

LL f[kMaxN], g[kMaxN], st[kMaxN], sp[kMaxN], n;
vector<LL> ans;

void F(LL l, LL r, LL wyy, LL zrr) {
  if (l > r) {
    return;
  }
  LL m = (l + r) / 2, best = wyy;
  f[m] = 1e18;
  for (LL i = wyy; i <= min(m, zrr); i++) {
    LL val = sp[m] * a[i].t - st[m] * a[i].p;
    if (val < f[m]) {
      f[m] = val;
      best = i;
    }
  }
  F(l, m - 1, wyy, best);
  F(m + 1, r, best, zrr);
}

void G(LL l, LL r, LL wyy, LL zrr) {
  if (l > r) {
    return;
  }
  LL m = (l + r) / 2, best = zrr;
  g[m] = -1e18;
  for (LL i = zrr; i >= max(m + 1, wyy); i--) {
    LL val = sp[m] * a[i].t - st[m] * a[i].p;
    if (val > g[m]) {
      g[m] = val;
      best = i;
    }
  }
  G(l, m - 1, wyy, best);
  G(m + 1, r, best, zrr);
}

int main() {
  cin.tie(0)->sync_with_stdio(0);
  cin >> n;
  for (LL i = 1; i <= n; i++) {
    cin >> a[i].t >> a[i].p;
  }
  sort(a + 1, a + n + 1, [](auto a, auto b) {
    return a.t * b.p > a.p * b.t;
  });
  for (LL i = 1; i <= n; i++) {
    st[i] = st[i - 1] + a[i].t;
    sp[i] = sp[i - 1] + a[i].p;
  }
  F(1, n - 1, 1, n);
  G(1, n - 1, 1, n);
  for (LL i = 1; i < n; i++) {
    if (f[i] < g[i]) {
      ans.push_back(n - i);
    }
  }
  reverse(ans.begin(), ans.end());
  cout << ans.size() << '\n';
  for (LL i : ans) {
    cout << i << '\n';
  }
  return 0;
}
```



