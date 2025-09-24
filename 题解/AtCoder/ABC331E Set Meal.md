#贪心

## 题目大意

有 $N$ 个主菜，第 $i$ 个主菜需要 $a_i$ 元；$M$ 个配菜，第 $i$ 个配菜 $b_i$ 元。但是有 $L$ 对主菜和配菜是不能配在一起的。一对菜的价值定义为主菜加上配菜价钱的和。问你最贵的一对菜需要多少元。

## 思路

我们先考虑一个暴力算法：首先枚举 $N$ 个主菜，然后枚举 $M$ 个配菜，最后遍历 $L$ 个配对，判断一下是否可以购买，然后记录最大值。这种算法的时间复杂度是 $\mathcal O(NML)$ 的，而 $1\le N,M,L\le 10^5$，使用这种算法会直接吃席。

我们可以来尝试优化一下，既然要求的是最大值，那么一个主菜必须配对可以买的的最大价值的配菜。那么我们可以直接对 $b$ 数组排序，然后从后往前遍历一遍，在来判断是否可以购买，如果可以就记录最大值，然后 break。这种做法虽然是三重循环，但是时间复杂度是 $\mathcal O(L^2)$ 的，因为第一二层循环只会枚举 $L$ 次，枚举完就必定可以找到可以配对的。

现在我们要加快判断是否能够购买的速度。可以使用一个集合，然后第三重循环就可以直接省掉——变成一个判断是否在集合内出现过的问题。这种算法的时间复杂度是 $\mathcal O(L\log_2\min(M,L))$ 的，因为一个集合内的元素最多有 $L$ 个，但是其实同样不能超过 $M$ 个，因此这题就过掉了。

## 代码

```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <set>

using namespace std;

int n, m, l, ans;

int main() {
  cin >> n >> m >> l;
  vector<int> a(n + 1);                  // 主菜
  vector<pair<int, int>> b(m + 1);       // 配菜
  vector<set<int>> s(n + 1, set<int>()); // 不能配对的菜
  for (int i = 1; i <= n; i++) {
    cin >> a[i];
  }
  for (int i = 1; i <= m; i++) {
    cin >> b[i].first, b[i].second = i;  // 输入并打上编号
  }
  sort(b.begin(), b.end(), [](const auto &a, const auto &b) {  // 排序
    return a.first < b.first;                                  // 按价格排序
  });
  for (int i = 1, x, y; i <= l; i++) {
    cin >> x >> y;
    s[x].insert(y);  // 买了主菜 x 不能买 y
  }
  for (int i = 1; i <= n; i++) {             // 枚举主菜
    for (int j = m; j >= 1; j--) {           // 枚举配菜
      if (!s[i].count(b[j].second)) {        // 如果可以购买
        ans = max(ans, a[i] + b[j].first);   // 记录最大值
        break;                               // 灵魂剪枝
      }
    }
  }
  cout << ans << '\n';  // 输出最优答案
  return 0;
}
```