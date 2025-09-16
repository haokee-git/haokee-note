#模拟 

## 题意简介

在一个 $n\times n$ 的矩阵里面，有一个人要一行一行蛇形爬过去。求一条路径 $l$，使得 $\sum\limits_{i=1}^{n^2-1}l_i>l_{i+1}$ 严格小于 
$\sum\limits_{i=1}^{n^2-1}l_{i}\le l_{i-1}$。

## 思路

我们可以枚举每一列，蛇形记录下路径。然后对路径进行枚举，分别记录正着要爬的台阶数量以及反着要爬的台阶数量，取最小值输出路径。

```cpp
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

const int kMaxN = 65;

int a[kMaxN][kMaxN], t, n, c1, c2;
vector<int> v;  // 使用vector记录路径

int main() {
  for (cin >> t; t; t--) {
    cin >> n, v.clear(), c1 = c2 = 0;  // 多测记得清空
    for (int i = 1; i <= n; i++) {
      for (int j = 1; j <= n; j++) {
        cin >> a[i][j];
      }
    }
    for (int i = 1; i <= n; i++) {
      if (i & 1) {  // 如果是奇数行
        for (int j = 1; j <= n; j++) {  // 正着走过去
          v.push_back(a[i][j]);
        }
      } else {  // 偶数行
        for (int j = n; j >= 1; j--) {  // 反着走过去
          v.push_back(a[i][j]);
        }
      }
    }
    for (int i = 0; i < n * n - 1; i++) { // 注意vector是从零开始的
      v[i] > v[i + 1] ? ++c1 : ++c2;  // c1,c2分别表示反着、正着走过去的台阶数
    }
    if (c1 < c2) {  // 如果反着更优
      for (int i = n * n - 1; i >= 0; i--) {  // 反向输出
        cout << v[i] << ' ';
      }
    } else {
      for (int i = 0; i < n * n; i++) {  // 正着输出
        cout << v[i] << ' ';
      }
    }
    cout << '\n';
  }
  return 0;
}
```