#背包dp #组合数学 #二项式定理 #幂  

## 解法

首先观察到极大的 $N$ $(1\le N\le 2\times 10^5)$，这似乎让我们无从下手，但是不难发现 $K$ 极小 $(1\le K\le 10)$，这不禁让我们想到 $K$ 是一个关键的突破口。

考虑 dp。令 $dp_{i,j}$ 表示为以第 $i$ 个元素为结尾的所有区间的的和的 $k$ 次方之和，即

$$
dp_{i,j}=\sum_{k=1}^i\left(\sum_{l=k}^i a_l\right)^K
$$

每次加入一个元素 $a_i$ 时，假设之前的和为 $S$，我们可以利用二项式定理

$$
(a+b)^k=\sum\limits_{i=0}^k\binom{k}{i}a^i\cdot b^{k-i}
$$

展开 $(S+a_i)^k$，即

$$
(S+a_i)^k=\sum\limits_{m=0}^k\binom{k}{m}S^m\cdot a_i^{k-m}
$$

可以发现这个式子里面的 $\binom{k}{m}$ 和 $a_i^{k-m}$ 都是可以通过预处理提前计算得到，而 $S^m$ 就是 $dp_{(i-1,m)}$。通过这种方式，我们可以递推得到 dp 数组。最后 $\sum\limits_{i=1}^N dp_{i,k}$ 就是答案了。注意取模。

## 复杂度分析

### 时间复杂度

读入 $\mathcal O(N)$，预处理组合数 $\mathcal O(K^2)$，预处理 $a_i^k$ $\mathcal O(NK)$，dp 过程 $\mathcal O(NK^2)$，总时间复杂度 $\mathcal O(NK^2)$。本题下 $1\le N\le 2\times 10^5,1\le K\le 10$，因此运算量级大概是 $2\times 10^7$ 级别的，可以通过。如果不预处理 $a_i^k$ 的话，时间复杂度 $\mathcal O(NK^2\log_2 K)$。

### 空间复杂度

$A$ 数组存储 $\mathcal O(N)$，组合数数组 $\mathcal O(K^2)$，$a_i^k$ 数组 $\mathcal O(NK)$，dp 数组 $\mathcal O(NK)$，总空间复杂度 $\mathcal O(NK)$。如果不处理 $a_i^k$ 数组并对 dp 数组进行滚动数组优化的话空间复杂度为 $\mathcal O(N+K^2)$。

## 代码

采用滚动数组优化 dp。

```cpp
#include <iostream>
#include <vector>

using namespace std;
using LL = long long;

const LL kMod = 998244353;

LL n, K, ans;

int main() {
  cin.tie(0)->sync_with_stdio(0);

  // 读入
  cin >> n >> K;
  vector<LL> a(n + 1);
  for (LL i = 1; i <= n; i++) {
    cin >> a[i];
  }

  // 预处理组合数
  vector<vector<LL>> C(K + 1, vector<LL>(K + 1));
  for (LL k = 0; k <= K; k++) {
    C[k][0] = 1;
    for (LL m = 1; m <= k; m++) {
      C[k][m] = (C[k - 1][m - 1] + C[k - 1][m]) % kMod;
    }
  }

  // 预处理 a[i]^k
  vector<vector<LL>> powA(n + 1, vector<LL>(K + 1));
  for (LL i = 1; i <= n; i++) {
    powA[i][0] = 1;
    LL x = a[i] % kMod;
    for (LL k = 1; k <= K; k++) {
      powA[i][k] = powA[i][k - 1] * x % kMod;
    }
  }

  // dp 过程及统计答案
  vector<LL> dp(K + 1);
  for (LL i = 1; i <= n; i++) {
    vector<LL> f(K + 1);
    for (LL k = 0; k <= K; k++) {
      for (LL m = 0; m <= k; m++) {
        LL trm = C[k][m] * powA[i][k - m] % kMod, prv = dp[m];
        if (m == 0) {  // 注意对零次方的特殊判断
          prv = (prv + 1) % kMod;
        }
        f[k] = (f[k] + trm * prv) % kMod;
      }
    }
    dp = f;
    ans = (ans + dp[K]) % kMod;
  }
  cout << ans << "\n";
  return 0;
}
```