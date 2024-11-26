#最大公因数 #前缀和 

先预处理 $\gcd(a_i, a_{i+1})$，存进 $b_i$，然后枚举删第 $i$ 个数，那么 $i$ 前面的相邻的最大公因数以及 $i$ 后面的相邻的最大公因数就必须递增。既然将 $i$ 删掉了，那么补充的元素就是 $\gcd(a_{i-1},a_{i+1})$，需要位于上一个 $b_i$ 和下一个 $b_i$ 的中间。

怎样快速求前缀或后缀 $b_i$ 都是单调非递增或单调非递减的呢？以前缀单调非递减举例，令 $p_i$ 表示 $1\sim i$ 当中的所有 $b_i$ 是否递增，那么求 $p_i$ 的时候如果 $p_{i-1}=0$ 就当然不满足条件啦，如果为真就看一下 $b_i$ 是否大于等于 $b_{i-1}$ 就行了。

```cpp
#include <iostream>

using namespace std;

const int kMaxN = 2e5 + 5;

int a[kMaxN], b[kMaxN], p[kMaxN], s[kMaxN], t, n, ans;

int gcd(int n, int m) {
  return !m ? n : gcd(m, n % m);
}

int main() {
  ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);
  for (cin >> t; t; t--) {
    cin >> n, ans = 0;
    for (int i = 1; i <= n; i++) {
      cin >> a[i];
    }
    p[0] = s[n] = 1, b[n] = 1e9;
    for (int i = 1; i < n; i++) {
      b[i] = gcd(a[i], a[i + 1]);
      p[i] = p[i - 1] && b[i] >= b[i - 1];
    }
    for (int i = n - 1; i; i--) {
      s[i] = s[i + 1] && b[i] <= b[i + 1];
    }
    for (int i = 1; i <= n; i++) { 
      ans |= (i <= 2 || p[i - 2]) &&
          (i >= n || s[i + 1]) &&
          (i == 1 || i == n || 
           (b[i - 2] <= gcd(a[i - 1], a[i + 1]) && 
            gcd(a[i - 1], a[i + 1]) <= b[i + 1]));
    }
    cout << (ans ? "YES" : "NO") << '\n';
  }
  return 0;
}
```