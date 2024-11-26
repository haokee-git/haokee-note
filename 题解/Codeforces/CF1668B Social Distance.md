#贪心 #排序

## 题目大意

- $n$ 个人要坐在 $m$ 个椅子组成的环上面；
- 第 $i$ 个人左右要空 $a_i$ 的位置；
- 判断能否坐下 $n$ 个人。
  
## 思路

既然是两个人互相空位置，那么两个人隔得位置越相近肯定就越好。我们直接排序一遍，这样子相邻的两个人必然空的位置大小最靠近。由于这些椅子组成了一个环，那么第 $1$ 个人就会挨着第 $n$ 个人。我们统计一下至少需要多少个位置，再判断是否匹配条件。

## 代码

```cpp
#include <iostream>
#include <algorithm>

using namespace std;
using ll = long long;  // 开long long

const int kMaxN = 5e4 + 1;

ll a[kMaxN], t, n, m, ans;

int main() {
  for (cin >> t; t; --t) {
    cin >> n >> m, ans = 0;
    for (int i = 1; i <= n; ++i) {
      cin >> a[i];
    }
    sort(a + 1, a + n + 1);  // 从小到大排序一遍
    for (int i = 1; i <= n; ++i) {
      ans += a[i == 1 ? n : i] + 1;  // 特判，记得加一
    }
    cout << (ans <= m ? "YES" : "NO") << '\n';  // 判断是否符合条件
  }
  return 0;
}
```