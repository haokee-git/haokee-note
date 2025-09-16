#枚举 

## 思路

首先，由于 $N$ 最大有 $2\times 10^5$，很显然我们不能通过枚举 $(a,b)$ 的方式进行处理，因为这种方式的时间复杂度至少为 $\mathcal O(n^2)$，因此我们需要更换枚举的方式。

对样例进行观察，很显然可以发现满足的数对 $(a,b)$ 当中，$a$ 和 $b$ 在原数组当中对应的位置都是相邻的。例如 $a=1,b=2$ 且满足条件，则可能是这样：

```cpp
…… 1 2 …… 1 2 ……
```

或者

```cpp
…… 2 1 …… 2 1 ……
```

还可以

```cpp
…… 2 1 …… 1 2 ……
```

即 $1$ 和 $2$ 都是相邻的。需要注意的是这种不行

```cpp
…… 1 2 2 1 ……
```

因为不能有相同的元素相邻。

结合上面的结论，我们就可以很简单地优化枚举方式了。由于有两对 $(a,b)$ 在原数组的位置是相邻的，因此我们只需要枚举相邻的元素，然后看一看是否符合条件就行了。我这里使用 vector 存储每个元素的两个位置。时间复杂度 $\mathcal O(n)$。

## 代码

```cpp
#include <iostream>
#include <vector>

using namespace std;

const int kMaxN = 1e6 + 5;

int a[kMaxN], t, n, ans;
vector<int> v[kMaxN];

int main() {
  cin.tie(0)->sync_with_stdio(0);
  for (cin >> t; t; t--) {
    // 读入和初始化
    cin >> n;
    fill(v + 1, v + n + 1, vector<int>());
    ans = 0;
    for (int i = 1; i <= 2 * n; i++) {
      cin >> a[i];
      v[a[i]].push_back(i);
    }

    // 处理
    for (int i = 1; i < 2 * n; i++) {
      if (a[i] != a[i + 1] && 
          abs(v[a[i]][0] - v[a[i]][1]) != 1 && 
          abs(v[a[i + 1]][0] - v[a[i + 1]][1]) != 1) {  // 要求相同的数不相邻，不相同的数相邻
        int x, y;  // 另外两个 (a,b) 的位置
        if (i == v[a[i]][0])  {
          x = v[a[i]][1];
        } else {
          x = v[a[i]][0];
        }
        if (i + 1 == v[a[i + 1]][0]) {
          y = v[a[i + 1]][1];
        } else {
          y = v[a[i + 1]][0];
        }
        if (abs(x - y) == 1) {  // 另外的也要相邻
          ans++;
        }
      }
    }
    cout << ans / 2 << '\n';  // 注意除以 2，因为这里一个 (a,b) 会枚举两次
  }
  return 0;
}
```