#序列dp 

补充一种非贪心的另类 dp 解法。

根据题目，不难发现只有 $l\sim r$ 的数字是有要求的，需要和为 $s$，而其它地方只需要把剩下的数填进去就行了。因此不妨令 $m=r-l+1$，那么就需要在 $1\sim n$ 当中选择 $m$ 个数加起来等于 $s$。

于是，我们便可以将这 $n$ 个数看成 $n$ 个物品，构造出 01 背包。令 $f_{i,j,k}$ 表示为在 $1\sim i$ 当中选择了 $j$ 个不同的数，加起来能否等于 $k$，那么这个数可以由 $n$ 个数转移来，便是 $f_{i,j,k}=\max\limits_{w=1}^n f_{i-1,j-1,k-w}$

但是这个办法需要开 $n\times m\times s$ 的数组，空间复杂度 $\mathcal O(n^4)$，而本题 $n\le 500$，自然会超出内存限制。但是，我们可以通过压数组的手段来讲第一维去掉。因为 $f_i$ 只会依赖 $f_{i-1}$，而 $j$ 这个维度也只会访问 $j-1$，因此我们只需要将 $j$ 倒序枚举即可。

这样做空间能够得到有效的优化，但时间复杂度仍然是 $\mathcal O(n^4)$。考虑优化时间，比如当答案 $f_{m,s}$ 已经计算出来了的时候，就退出 dp。但是最有效的方法还是直接在循环外面判断解是否合法，如果 $1\sim m$ 加起来都比 $m$ 大或者 $n-m+1\sim n$ 加起来都比 $s$ 要小，那么肯定是满足不了条件的，因此直接输出无解。

注意这题需要输出答案，因此 dp 需要记录前驱状态。但是实际上并不用开两个数组，只需要记录当前状态是加了多少就行了。一秒半大常数过题。

```cpp
#include <iostream>
#include <set>

using namespace std;

const int kMaxN = 505, kMaxS = kMaxN * (kMaxN + 1) / 2;

int dp[kMaxN][kMaxS], f[kMaxN], p, t, n, m, l, r, s;
set<int> st;

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> l >> r >> s;
    m = r - l + 1, p = 1;
    if ((n - m + 1 + n) * m / 2 < s || (1 + m) * m / 2 > s) {
      cout << "-1\n";
      continue;
    }
    fill(f + 1, f + n + 1, 0);
    for (int i = 1; i <= m; i++) {
      for (int j = i; j <= s; j++) {
        dp[i][j] = 0;
      }
    }
    dp[0][0] = 1, st.clear();
    for (int i = 1; i <= n; i++) {
      if (dp[m][s]) {
        break;
      }
      for (int j = min(m, i); j >= 1; j--) {
        for (int k = i; k <= min(s, i * (i + 1) / 2); k++) {
          dp[j - 1][k - i] && !dp[j][k] && (dp[j][k] = i);
        }
      }
    }
    for (int i = 1; i <= n; i++) {
      st.insert(i);
    }
    for (int i = m, j = s; i; j -= dp[i][j], i--) {
      f[l + i - 1] = dp[i][j];
      st.erase(dp[i][j]);
    }
    for (int i = 1; i <= n; i++) {
      if (f[i]) {
        cout << f[i] << ' ';
      } else {
        cout << *st.begin() << ' ';
        st.erase(st.begin());
      }
    }
    cout << '\n';
  }
  return 0;
}
```