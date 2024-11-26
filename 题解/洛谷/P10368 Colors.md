#模拟

提供一种另类的模拟算法，适用于更多的情况（而不一定为 $\texttt{aba}$ 式，虽然赛后才发现最多只会删除两次）。

如果一次操作没有删除任何数的话，那么这次操作是毫无意义的，因此操作最多执行 $n$ 次。为了快速删除一个数，我们可以使用链表的结构。那么这样子的时间复杂度是 $\mathcal O(n^2)$ 的，仍然不优。

仔细观察，删除第 $i$ 个字符只会影响第 $i-1$ 个字符和第 $i+1$ 个字符，因此删除了之后直接对这两个进行判定就行了。但是我们需要考虑复杂一点的情况，假如有若干个需要删除的连续字符，那么我们只删除了一个就去对前一个字符作判定是不对的，因为后面的字符还没有删掉。

考虑新加一个 wait 数组，我们先把需要删的删掉了再来判断这些需要判断的数，而 wait 数组就是用来存储这些数的。这样，我们就可以愉快地使用 $\mathcal O(n)$ 的算法通过了。

```cpp
#include <iostream>
#include <vector>

using namespace std;

const int kMaxN = 1e7 + 5;

int prv[kMaxN], nxt[kMaxN], b[kMaxN], t, id, n;  // prv 是上一个元素，nxt 是下一个，b 是标记数组
long long k;                                     // 最多删除次数，注意使用 long long
vector<int> v, f, wait;                          // 分别为上一次删的，下一步要删的和 wait 数组
char s[kMaxN];                                   // 用来存储字符串

// 判断第 x 个字符是否满足条件
bool check(int x) { return s[nxt[x]] == s[prv[x]]; }

int main() {
  ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);  // 读入优化
  for (cin >> t >> id; t; t--) {                     // 多组数据
    cin >> n >> k >> (s + 1);                        // 输入信息
    f.clear();                                       // 清空第一次要删的
    // 初始化链表
    for (int i = 1; i <= n; i++) {
      prv[i] = i - 1, nxt[i] = i + 1;
    }
    // 第一次删除（没有真正删掉）
    for (int i = 2; i <= n; i++) {
      check(i) && (f.push_back(i), 0);
    }
    // 最多 k 次并且有要删的
    for (int i = 1; i <= k && f.size(); i++) {
      wait.clear();      // 清空 wait 数组
      for (int j : f) {  // 遍历要删的
        b[j] = 1;        // 真正删除
      }
      // 执行下一步删除
      for (int j = 0, k; j < f.size(); ) {
        for (k = j + 1; k < f.size() && f[k] - f[k - 1] == 1; k++) { }  // 找到一段连续的 [j, k)
        nxt[prv[f[j]]] = nxt[f[k - 1]];                                 // 对链表进行删除操作
        prv[nxt[f[k - 1]]] = prv[f[j]];
        wait.push_back(prv[f[j]]);                                      // 加入 wait 数组
        wait.push_back(nxt[f[k - 1]]);
        j = k;                                                          // 跳过去
      }
      // 对 wait 进行逐一排查
      for (int j : wait) {
        if (!b[j] && 1 < j && j < n && check(j)) {  // 如果满足条件
          v.push_back(j);                           // 加入下一步要删的
        }
      }
      f = v, v.clear();                             // 交换并清空
    }
    // 输出并清空
    for (int i = 1; i <= n; b[i++] = 0) {
      if (!b[i]) {
        cout << s[i];
      }
    }
    cout << '\n';
  }
  return 0;
}
```