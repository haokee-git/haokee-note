#位运算 

## 题目大意

给定 $a,b$ 和 $C$，现在要你找到两个正整数 $x$ 和 $y$，使得 $x$ 的对应二进制数当中 $1$ 的个数为 $a$，$y$ 的对应二进制当中 $1$ 的个数为 $b$，以及 $x\oplus y=C$。

## 解法

首先，我们知道 $x\oplus 0=x$ 和 $x\oplus x=0$，然后考虑构造方案。不如先令 $x=C,y=0$，那么很显然 $x\oplus y=C$。接下来考虑如何满足条件一二，我们可以将 $x$ 的一些位置上面的 $1$ 移动到 $y$ 上面，这样子 $x\oplus y$ 仍等于 $C$。但是有可能位数不够用，这时候我们就需要找到一些 $x$ 和 $y$ 都等于 $0$ 的位置，然后把这个位置上面的数都改成 $1$，这样子 $x\oplus y$ 也是等于 $C$ 的。

为了让他们尽量匹配，在把 $x$ 的 $1$ 移到 $y$ 身上的时候，我们需要尽量的匀称，简单来说就是让 $a-\text{popcount(x)}$ 尽量接近 $b-\text{popcount}(y)$。

具体操作请看代码。

## 代码

```cpp
#include <iostream>
#include <bitset>

using namespace std;
using LL = unsigned long long;

const LL kMaxN = 2e5 + 5;

LL a, b, c;
bitset<60> x, y;

int main() {
  cin >> a >> b >> c;
  x = c;                                      // 先令 x = c
  LL cnt = 0, res = (x.count() + b - a) / 2;  // 计算需要移多少个
  for (LL i = 0; cnt < res && i < 60; i++) {  // 移动 res 次
    if (x[i]) {                               // 如果可以移
      x[i] = 0, y[i] = 1;                     // 移过去
      cnt++;                                  // 计数器累加
    }
  }
  cnt = 0, res = a - x.count();               // 清空并计算要填多少个 1
  for (LL i = 0; cnt < res && i < 60; i++) {  // 填 1
    if (!x[i] && !y[i]) {                     // 找空的地方填
      x[i] = y[i] = 1;                        // 填上去
      cnt++;                                  // 计数器累加
    }
  }
  if (x.count() != a || y.count() != b || (x.to_ullong() ^ y.to_ullong()) != c) {
    cout << "-1\n";
  } else {
    cout << x.to_ullong() << ' ' << y.to_ullong() << '\n';
  }
  return 0;
}
```