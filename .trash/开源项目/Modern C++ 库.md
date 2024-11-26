[link](https://git.rbtr.ee/haokee/ModernCpp)

此库可以让你的 C++ 代码风格更接近其他现代编程语言的代码风 格，并手写了 C++ 23 下大多数人还不能使用的 print 系列函数（目前只支持最基本的占位符）。

## 安装

在 [版本发布 - ModernCpp](https://git.rbtr.ee/haokee/ModernCpp/releases) 下下载最新的 ModernCpp.zip（或其它格式的压缩包）文件，然后跟你的源代码目录放在同一个文件夹下（譬如你的需要使用此库的源代码文件在桌面，那么就将压缩包里面的文件放在桌面），在源代码里加入 `#include "all"` 并开启 C++11 或更高版本进行编译即可食用（保证 [[GCC]] 和 [[MSVC]] 加入编译选项可以成功通过编译）。可以拿实例来判断是否配置成功。

如果你只想快速食用的话，可以尝试把这个压行版放进你的源代码：

```cpp
#include <iostream>
#include <string>
#define var auto
#define val const auto
#define let constexpr auto
void print(std::string fmt){std::cout<<fmt;}template<class T>void print(std::string fmt,T x){for(size_t i=0ull;i<fmt.size();i++){if(i<fmt.size()-1&&fmt[i]=='{'&&fmt[i+1]=='}'){std::cout<<std::to_string(x);i++;}else{std::cout<<fmt[i];}}}template<class T,class...More>void print(std::string fmt,T x,More...more){size_t p=-1;for(size_t i=0ull;i<fmt.size();i++){if(i<fmt.size()-1&&fmt[i]=='{'&&fmt[i+1]=='}'){std::cout<<std::to_string(x);p=i+2;break;}else{std::cout<<fmt[i];}}if(p!=size_t(-1)&&p<fmt.size()){print(fmt.substr(p,fmt.size()-p),more...);}}template<class...More>void println(More...more){print(more...);print(std::string("\n"));}struct{void operator()(){}template<class T>void operator()(T&x){std::cin>>x;}template<class T,class...More>void operator()(T&x,More&...more){operator()(x);operator()(more...);}template<class T>operator T(){T x;std::cin>>x;return x;}template<class T>T get(){return(T)(*this);}}read;
```

## 内容

### conversion.hpp

用于提供并实现部分 print.hpp 需要的占位符的 toString 函数接口。对于所有的 toString 函数，假如要转换的数据类型为 T，那么其参数列表应该为如下形式：

```cpp
std::string toString(std::string fmt, T n) { }
```

其中 fmt 是占位符的具体形式（不包括两边的大括号）。返回的 string 就是 print 会进行替换的实际内容。

### print.hpp

类似 C++23 的 print 函数，只是功能少一些。使用 `{}` 作为占位符，原版特性：[std::print - cppreference.com](https://en.cppreference.com/w/cpp/io/print)。这个版本是好渴鹅自己手写的版本，占位符的原理就是通过 conversion.hpp 里提供的接口 toString(string, T) 来进行转换。可以对 toString 进行重载来达到输出自己的类型的效果。

除了对 float/double 特殊占位符判断外，其他类型都是直接调用 std::to_string 来解决的。浮点数的占位符支持 `{x}` 输出 xx 位有效位数，`{.x}` 四舍五入 xx 位。

### read.hpp

支持三种输入方式：

```cpp
var/val a = read.get<type>(), b = read.get<type>();

type a = read, b = read;

type a, b;
read(a, b);
```

var/val 见 variable.hpp

### variable.hpp

定义了类似 Kotlin 等的变量定义方式。具体地：

```cpp
#define var auto
#define val const auto
#define let constexpr auto
```

需要注意的是编译时常量使用的是 let。

### all

包含了本库的所有头文件。

## 示例

```cpp
#include "all"

using namespace std;

int main() {
  val a = read.get<int>(), b = read.get<int>();
  println("{}+{}={}", a, b, a + b);

  int c = read, d = read;
  println("{}+{}={}", c, d, c + d);

  int e, f;
  read(e, f);
  println("{}+{}={}", e, f, e + f);
  
  int n = read;
  foreach(1, n, [](val x) {
    print("{} ", x);
  });
  return 0;
}
```

终端输入：

```cpp
1 1
1 1
1 1
10
```

终端输出：

```cpp
1+1=2
1+1=2
1+1=2
1 2 3 4 5 6 7 8 9
```