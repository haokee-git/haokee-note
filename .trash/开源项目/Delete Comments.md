[Delete Comments](https://git.rbtr.ee/haokee/DeleteComments)是一个使用 C++ 编写的、用来删除 C/C++ 注释的工具，支持单行注释与多行注释。由于目前是测试版本，删除代码（`src/delcom.cpp`）可能有 bug，请去「工单」页面反馈。
## 选项

- `delcom file`：删除 `file` 文件的注释，并在终端输出删除后的内容；
- `delcom file output_file`：删除 `file` 文件的注释，并在将结果输出到 `output_file` 里。

## 样例

原始文件（`test/main.cpp`）如下：

```cpp
// haokee
#include <iostream>

/*using namespace std;
*/
int main() {
  /*abc*/std::cout << "ctrl"; /*dddd
  ddddddddddddd
  ddddd*/
  return /*(0^0)*/0;  // cute
}
```

运行 `delcom main.cpp` 的输出如下：

```cpp
#include <iostream>
 

int main() {
  std::cout << "ctrl";
  return 0;
}
```

## 源代码

主程序的源代码在 `src/` 下，测试文件的源代码在 `test/`，CMake 工程文件（包括原始编译出的可执行文件）在 `build/` 下。