#模拟

枚举 $x$，那么剩下的所有数当中最大的那个就一定是 $a_i\sim a_n$ 的和，因为 $1\le b_i\le 10^9$，$a$ 同理。判断一下剩下的那个数是否合法就行了。

```cpp
#include <iostream>
#include <set>

using namespace std;
using LL = long long;

const LL kMaxN = 2e5 + 5;

LL a[kMaxN], t, n, sum, ans1, ans2;
multiset<LL> s;

int main() {
  for (cin >> t; t; t--) {
    cin >> n;
    sum = 0, ans1 = -1;
    s.clear();
    for (LL i = 1; i <= n + 2; i++) {
      cin >> a[i];
      s.insert(a[i]);
      sum += a[i];
    }
    for (LL i = 1; i <= n + 2; i++) {
      s.erase(s.find(a[i]));
      if (*s.rbegin() == sum - a[i] - *s.rbegin()) {
        ans1 = a[i];
        ans2 = *s.rbegin();
        break;
      }
      s.insert(a[i]);
    }
    if (!~ans1) {
      cout << "-1\n";
      continue;
    }
    for (LL i = 1; i <= n + 2; i++) {
      if (a[i] == ans1) {
        ans1 = 0;
      } else if (a[i] == ans2) {
        ans2 = 0;
      } else {
        cout << a[i] << ' ';
      }
    }
    cout << '\n';
  }
  return 0;
}
```