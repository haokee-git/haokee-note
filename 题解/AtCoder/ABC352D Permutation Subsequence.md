#序列最大值查询 

这题需要找一个跨度最小的排序后相邻两个数差值为 $1$ 且长度为 $K$ 的子序列，但是由于子序列不一定是连续的，因此从下标入手很难做出来。不如换个思路：从值入手。

令 $f_i$ 表示 $i$ 在原数组当中的下标，那么 $f_a\sim f_{a+k-1}$ 便是任意满足条件的子序列当中每一个数的下标。因此，我们只需要计算对于每一个 $a$，$f_a\sim f_{a+k-1}$ 当中最大值与最小值的差值就行了。

看到很多人都为了求区间最值而写了线段树和 ST 表，实际上只需要使用 set 就行了，代码极短。时间复杂度：$\mathcal O(n\log_2 n)$。

```cpp
#include <iostream>
#include <set>

using namespace std;

const int kMaxN = 2e5 + 5;

int f[kMaxN], n, k, ans = 1e9;
set<int> s;

int main() {
  cin >> n >> k;
  for (int i = 1, x; i <= n; i++) {
    cin >> x;
    f[x] = i;
  }
  for (int i = 1; i <= n; i++) {                // 遍历
    s.insert(f[i]);                              // 将这个元素的下标加入 set
    if (i >= k) {                                // 如果已经塞了 k 个元素
      ans = min(ans, *s.rbegin() - *s.begin());  // 计算最小差值
      s.erase(f[i - k + 1]);                     // 删除最前面的那个数
    }
  }
  cout << ans << '\n';
  return 0;
}
```