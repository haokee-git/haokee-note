#贪心

我们发现 字串 `map` 与 `pie` 进行重叠的方式只有 `map` 在 `pie` 前面并且同时使用了 `p`，因此我们只用删除字串的 `p` 部分。

```cpp
#include <iostream>
#include <string>

using namespace std;

int t, n, ans;
string s;

int main() {
  for (cin >> t; t; t--) {
    cin >> n >> s, ans = 0;
    s = ' ' + s;
    for (int i = 1; i <= n; i++) {
      if (i <= n - 2 && s[i] == 'p' && s[i + 1] == 'i' && s[i + 2] == 'e' ||
          i >= 2     && s[i] == 'p' && s[i - 1] == 'a' && s[i - 2] == 'm') {
        s[i] = ' ';
        ans++;
      }
    }
    cout << ans << '\n';
  }
  return 0;
}
```