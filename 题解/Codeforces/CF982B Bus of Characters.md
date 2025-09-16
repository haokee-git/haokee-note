#优先队列 #贪心

## 思路

既然每次都是坐在最值上面，那么我们就可以定义两个优先队列，分别存上内向者和外向者的座位信息，需要的时候就可以 `top` 出来最大或最小的座位。

由于堆顶的值 `top` 出来实际上是座位的宽度，因此通过所有的 $w_i$ 都不相同的特性，我们可以使用 [[map]] 或者 `unordered_map` 来存储位置编号。

**优先队列介绍：**[Oi - Wiki](https://oi-wiki.org/lang/csl/container-adapter/#%E4%BC%98%E5%85%88%E9%98%9F%E5%88%97)，[Cppreference](https://en.cppreference.com/w/cpp/container/priority_queue)，本质上就是一个堆。

## 代码

```cpp
#include <iostream>
#include <queue>  // 优先队列
#include <unordered_map>  // 哈希表

using namespace std;

int n, v;
char c;
priority_queue<int, vector<int>, greater<int>> q1;  // 小根堆，存储内向者
priority_queue<int, vector<int>, less<int>> q2;  // 小根堆，存储内向者
unordered_map<int, int> f;  // 哈希表

int main() {
  cin >> n;
  for (int i = 1; i <= n; ++i) {
    cin >> v;
    f[v] = i, q1.push(v);  // 存储进小根堆以及哈希表
  }
  for (int i = 1; i <= n << 1; ++i) {
    cin >> c;
    if (c == '0') {  // 内向者
      cout << f[q1.top()] << ' ';  // 输出堆鼎的编号
      q2.push(q1.top()), q1.pop();  // 这个位置只能坐外向者了
    } else {  // 外向者
      cout << f[q2.top()] << ' ';  
      q2.pop();  // 这个位置满了
    }
  }
  return 0;
}
```

## 思路 2

我们可以想，内向者既然选了一个最小的位置，那么最后一个内向者必然坐着有人当中最大的位置，然后外向者正好需要选择有人当中最大的位置，那不就是单调栈吗？

**单调栈介绍：**[Oi - Wiki]([单调栈 - OI Wiki (oi-wiki.org)](https://oi-wiki.org/ds/monotonous-stack/))，本质上就是满足一定顺序的栈。

## 代码

```cpp
#include <iostream>
#include <algorithm>  // sort
#include <stack>  // 栈
#include <unordered_map>  // 哈希表

using namespace std;

const int kMaxN = 2e5 + 1;

int a[kMaxN], n, p;
char c;
stack<int> s;
unordered_map<int, int> f;

int main() {
  cin >> n;
  for (int i = 1; i <= n; ++i) {
    cin >> a[i], f[a[i]] = i;  // 读入并存进哈希表
  }
  sort(a + 1, a + n + 1);  // 按座位宽度排序
  for (int i = 1; i <= n << 1; ++i) {
    cin >> c;
    if (c == '0') {
      cout << f[a[++p]] << ' ';  // 选择下一个座位
      s.push(a[p]);  // 这个座位坐了内向者
    } else {
      cout << f[s.top()] << ' ';  // 输出栈顶元素
      s.pop();  // 出栈
    }
  }
  return 0;
}
```