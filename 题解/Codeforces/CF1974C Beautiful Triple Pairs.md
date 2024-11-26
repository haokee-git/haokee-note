#组合数学 

一种比较通俗易懂的解法。

我们将需要相等的分为一组，也就是对应两个相等的性质，然后在每组里面分别进行统计：需要满足另外一个数不相等，那么我们只需要将答案累加这个数的数量乘上其他不同的数的数量就行了。

注意这种统计方法会双向统计，因此答案在输出的时候需要除以 $2$。

```cpp
#include <iostream>
#include <utility>
#include <map>

using namespace std;
using LL = long long;

const LL kMaxN = 2e5 + 5;

LL a[kMaxN], t, n, ans;
map<pair<LL, LL>, map<LL, LL>> f;  // 每一组里面的每一个数的记数
map<pair<LL, LL>, LL> c;           // 每一组里面元素数量

void solve(int x1, int x2, int x3) {         // x1 和 x2 满足等于，x3 满足不等于
  f.clear(), c.clear();                      // 清空
  for (LL i = 1; i <= n - 2; i++) {          // 遍历每一个三元组
    f[{a[i + x1], a[i + x2]}][a[i + x3]]++;  // 分组并加入
    c[{a[i + x1], a[i + x2]}]++;
  }
  for (auto &i : f) {                             // 遍历每一组
    for (auto &j : i.second) {                    // 遍历这一组里面的所有数
      ans += j.second * (c[i.first] - j.second);  // 当前数的数量乘上其他数的数量
    }
  }
}

int main() {
  for (cin >> t; t; t--) {
    cin >> n, ans = 0;
    for (LL i = 1; i <= n; i++) {
      cin >> a[i];
    }
    solve(0, 1, 2);           // 对于不同的限制分类求答案
    solve(0, 2, 1);
    solve(1, 2, 0);
    cout << ans / 2 << '\n';  // 注意除以二
  }
  return 0;
}
```