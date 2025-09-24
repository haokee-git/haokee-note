#后缀和 #排序 

## 题目大意

给我一个长度为 $N$ 的序列 $A$，第 $i$ 个数的值为 $A_i$。对于 $A_i$，你需要求出比 $A_i$ 大的数的和。

## 思路

我们首先将数组排序，注意要记录编号，因为这题需要输出所有的答案。排完序之后，我们就从后往前做一个后缀和，因为 $A_{(i+1)}$ 一定大于等于 $A_i$。注意这里需要特殊处理一下等于的情况，使用 $l$ 记录等于了几个数，$x$ 表示等于的是几。然后统计到 $ans$ 数组就行了。

注意这题要开 `long long`，不然会 WA。

## 代码

```cpp
#include <iostream>
#include <algorithm>

using namespace std;
using ll = long long;

const ll kMaxN = 2e5 + 5;

struct Node {
  ll v, id;  // 值和编号
} a[kMaxN];

ll p[kMaxN], ans[kMaxN], n, l, x;  // p 是后缀和数组，ans 是答案数组

int main() {
  cin >> n;
  for (ll i = 1; i <= n; i++) {
    cin >> a[i].v, a[i].id = i;  // 输入并记录编号
  }
  sort(a + 1, a + n + 1, [](const Node &a, const Node &b) {  // 排序
    return a.v < b.v;                                        // 根据值来排序
  });
  p[n] = 0;                                   // 第 n 个元素没有更大的值
  for (ll i = n - 1; i >= 1; i--) {           // 从后往前枚举
    if (a[i].v == a[i + 1].v) {               // 如果是等于的情况
      p[i] = p[i + 1];                        // 直接赋值过来
      l++, x = a[i].v;                        // 等于的长度加一，并记录下等于的值
    } else {                                  // 如果不是等于的情况
      p[i] += p[i + 1] + a[i + 1].v + l * x;  // 那么把之前的全部累加起来
      l = x = 0;                              // 清空
    }
  }
  for (ll i = 1; i <= n; i++) {
    ans[a[i].id] = p[i];  // 记录答案
  }
  for (ll i = 1; i <= n; i++) {
    cout << ans[i] << ' ';  // 输出答案
  }
  return 0;
}
```