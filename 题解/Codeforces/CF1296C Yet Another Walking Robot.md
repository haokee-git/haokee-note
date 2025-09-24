#模拟

我们可以发现，如果一段路径可以省略，那么这段路径走之前和走之后的位置会是一样的。因此我们可以使用 STL 当中的 [[map]] 来记录上一次走到这个位置的时间。因为是要求最短的区间，因此选择最小值就可以了。时间复杂度 $\mathcal O(n\log_2 n)$。

```cpp
#include <iostream>
#include <map>

using namespace std;

const int kMaxN = 2e5 + 5;

int t, n, x, y, l, r, mn;
map<pair<int, int>, int> f;  // 记录最后一次达到的时间
char c;

int main() {
  for (cin >> t; t; t--) {
    cin >> n;
    x = y = 0, mn = 1e9;  // 清零
    f.clear();            // 清空容器
    f[{x, y}] = 0;        // 初始时在 (0, 0)
    for (int i = 1; i <= n; i++) {
      cin >> c;
      x = x - (c == 'L') + (c == 'R');              // 移动 x
      y = y + (c == 'U') - (c == 'D');              // 移动 y
      if (f.count({x, y}) && i - f[{x, y}] < mn) {  // 如果已经记录过并且比答案更优
        mn = i - f[{x, y}];                         // 修改答案
        l = f[{x, y}] + 1, r = i;                   // 记录位置
      }
      f[{x, y}] = i;                                // 更新
    }
    if (mn == 1e9) {
      cout << "-1\n";
    } else {
      cout << l << ' ' << r << '\n';
    }
  }
  return 0;
}
```