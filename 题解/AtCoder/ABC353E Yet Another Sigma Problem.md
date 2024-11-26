#字典树 #模拟

看到字符串的前缀累加和，果断写字典树。字典树，就是第 $i$ 层结点代表第 $i$ 个字符，而每个结点的父亲就是上一个字符，儿子就是下一个父亲的所有可能。

拿样例来举例。首先，我们的第一个字符有多种不同的可能，我们当然不能开 $26$ 棵字典树，而是拿额外一个没有用的结点来充当树根。注意我们的字典树需要记录每个点的点权，用来统计答案。然后我们加入 $\texttt{ab}$，那么首先第一个字符 $\texttt{a}$ 不存在，那么我们就额外新建一个结点；第二个字符 $b$ 也不存在，就再新建一个结点。将路上的每一个结点权值都加 $1$。

然后是第二个字符串 $\texttt{abc}$，由于 $\texttt{ab}$ 已经是第一个串的前缀，那么答案就需要加 $2$。最后一个字符 $\texttt{c}$ 在 $\texttt{ab}$ 的后面不存在，那么我们就新建一个结点。将路上的每一个结点权值都加 $1$。

最后是 $\texttt{arc}$。$\texttt{a}$ 这个前缀在之前出现了 $2$ 次，那么答案就需要加 $2$。然后 $\texttt{r}$ 和 $\texttt{c}$ 都不存在，那么就需要新建结点。将路上的每一个结点权值都加 $1$。

答案：$2+2=4$。

```cpp
#include <iostream>

using namespace std;
using LL = long long;

const LL kMaxN = 3e5 + 5;

LL tr[kMaxN], nxt[kMaxN][26], n, cnt = 1, ans;  // cnt 初始化为 1，因为需要一个额外的根
string s;

void add(const string &s) {                     // 加入字符串 s
  LL p = 1;
  for (char c : s) {                            // 遍历每一个字符
    if (!nxt[p][c - 'a']) {                     // 如果不存在
      p = nxt[p][c - 'a'] = ++cnt;              // 新申请一个儿子
    } else {                                    // 已经存在
      p = nxt[p][c - 'a'];                      // 直接跳过去
    }
    ans += tr[p];                               // 累加答案
    tr[p]++;                                    // 路径上的数加一
  }
}

int main() {
  cin >> n;
  for (LL i = 1; i <= n; i++) {
    cin >> s;
    add(s);
  }
  cout << ans << '\n';
  return 0;
}
```