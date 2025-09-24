#贪心 #枚举

## 思路

首先我们可以很轻松地写出一个 $\mathcal O(n^3)$，大约就是先枚举左边界，然后用两个 [[vector]] 模拟子串两边的数字，再用一个循环判断是否相等。但是这样子会超时。我们发现判断字符串相等很慢，因此可以加入一个很简单的优化：如果当前产生的答案不会更优的话就不判断。时间复杂度为 $\mathcal O(|s|^2)$。

## 代码

```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

int t, head, ans;
string s;
vector<int> l, r;

bool check() {
  for (int i = 0; head + i < r.size(); i++) {
    if (l[i] != r[head + i] && l[i] != '?' && r[head + i] != '?') {
      return 0;
    }
  }
  return 1;
}

int main() {
  for (cin >> t; t; t--) {
    cin >> s, ans = 0;
    for (int i = 0; i < s.size(); i++) {
      head = 0, l.clear(), r.clear();
      for (int j = i + 1; j < s.size(); j += 2) {
        r.push_back(s[j - 1]), r.push_back(s[j]);
        l.push_back(r[head]), head++;
        j - i + 1 > ans && check() && (ans = max(ans, j - i + 1));
      }
    }
    cout << ans << '\n';
  }
  return 0;
}
```