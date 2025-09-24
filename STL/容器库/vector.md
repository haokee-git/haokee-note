vector 是一种常用的容器类，在 C++ 当中普遍用作变长数组。

## 定义

```cpp
template <class T,
          class Allocator = std::allocator<T>> 
class vector  // In namespace std
```

## 成员类型

### value_type

```cpp
using value_type = _Ty;
```

元素类型。

### allocator_type

```cpp
using allocator_type = _Alloc;
```

内存分配器类型。

### pointer

```cpp
using pointer = typename _Alty_traits::pointer;
```

指针类型。

### const_pointer

```cpp
using const_pointer = typename _Alty_traits::const_pointer;
```

常量指针类型。

### reference

```cpp
using reference = _Ty&;
```

引用类型。

### const_reference

```cpp
using const_reference = const _Ty&;
```

常量引用类型。

### size_type

```cpp
using size_type = typename _Alty_traits::size_type;
```

长度类型。

### difference_type

```cpp
using difference_type = typename _Alty_traits::difference_type;
```

差异类型。

### iterator

```cpp
using iterator = _Vector_iterator<_Scary_val>;
```

迭代器类型。

### const_iterator

```cpp
using const_iterator = _Vector_const_iterator<_Scary_val>;
```

常量迭代器类型。

### reverse_iterator

```cpp
using reverse_iterator = _STD reverse_iterator<iterator>;
```

反向迭代器类型。

### const_reverse_iterator

```cpp
using const_reverse_iterator = _STD reverse_iterator<const_iterator>;
```

反向常量迭代器类型。

## 成员函数

### 构造函数

```cpp
vector()
```

直接构造空的 vector。

```cpp
explicit vector(const _Alloc& _Al) noexcept
```

从内存分配器构造 vector。

```cpp
explicit vector(_CRT_GUARDOVERFLOW const size_type _Count, const _Alloc& _Al = _Alloc())
```

给定长度和内存分配器构造 vector。

```cpp
vector(_CRT_GUARDOVERFLOW const size_type _Count, const _Ty& _Val, const _Alloc& _Al = _Alloc())
```

给定长度、值和内存分配器构造 vector。

```cpp
vector(_Iter _First, _Iter _Last, const _Alloc& _Al = _Alloc())
```

给定迭代器左闭右开区间和内存分配器构造 vector。

```cpp
vector(initializer_list<_Ty> _Ilist, const _Alloc& _Al = _Alloc())
```

列表初始化并给定内存分配器构造 vector。

```cpp
vector(const vector& _Right)
```

从另一个 vector 构造 vector。

```cpp
vector(const vector& _Right, const _Identity_t<_Alloc>& _Al)
```

从另一个 vector 根据内存分配器构造 vector。

```cpp
vector(vector&& _Right) noexcept
```

从右值 vector 构造 vector。

```cpp
vector(vector&& _Right, const _Identity_t<_Alloc>& _Al_) noexcept(_Alty_traits::is_always_equal::value)
```

从右值 vector 给定内存分配器构造 vector。

### 析构函数

```cpp
~vector()
```

析构 vector 时调用。

### push_back

```cpp
void push_back(const _Ty& _Val)
```

在 vector 末尾插入一个新元素。

```cpp
void push_back(_Ty&& _Val)
```

在 vector 末尾插入一个新元素（右值引用）。

### emplace

```cpp
iterator emplace(const_iterator _Where, _Valty&&... _Val)
```

在一个位置构造元素并插入。

### insert

```cpp
iterator insert(const_iterator _Where, const _Ty& _Val)
```

在一个位置插入元素。

```cpp
iterator insert(const_iterator _Where, _Ty&& _Val)
```

在一个位置插入元素（右值引用）。

```cpp
iterator insert(const_iterator _Where, const size_type _Count, const _Ty& _Val)
```

在一个位置插入多个同样的元素。

```cpp
iterator insert(const_iterator _Where, _Iter _First, _Iter _Last)
```

在一个位置插入一个迭代器左闭右开区间的元素。

```cpp
iterator insert(const_iterator _Where, initializer_list<_Ty> _Ilist)
```

在一个位置插入一个列表。

### assign

```cpp
void assign(_CRT_GUARDOVERFLOW const size_type _Newsize, const _Ty& _Val)
```

将某一长度的元素替换为指定元素。

### resize

```cpp
void resize(_CRT_GUARDOVERFLOW const size_type _Newsize)
```

将 vector 清空为指定长度的空元素。

```cpp
void resize(_CRT_GUARDOVERFLOW const size_type _Newsize, const _Ty& _Val)
```

将 vector 清空为指定长度，并初始化为给定元素。

### reserve

```cpp
void reserve(_CRT_GUARDOVERFLOW size_type _Newcapacity)
```

预先分配指定长度的空间。

### pop_back

```cpp
void pop_back() noexcept
```

弹出最后一个元素，vector 不能为空。

### erase

```cpp
iterator erase(const_iterator _Where) noexcept(is_nothrow_move_assignable_v<value_type>)
```

删除一迭代器上的元素。

```cpp
iterator erase(const_iterator _First, const_iterator _Last) noexcept(is_nothrow_move_assignable_v<value_type>)
```

删除迭代器左闭右开区间的元素。

### clear

```cpp
void clear() noexcept
```

清空 vector。

### swap

```cpp
void swap(vector& _Right) noexcept
```

与另一个 vector 交换。

### data

```cpp
_Ty* data() noexcept
```

返回元素实际存储的位置。

```cpp
const _Ty* data() const noexcept
```

返回元素实际存储的位置（常量指针）。

### begin

```cpp
iterator begin() noexcept
```

返回第一个元素的迭代器。

```cpp
const_iterator begin() const noexcept
```

返回第一个元素的只读迭代器。

### end

```cpp
iterator end() noexcept
```

返回最后一个元素的后面一个元素的迭代器。

```cpp
const_iterator end() const noexcept
```

返回最后一个元素的后面一个元素的只读迭代器。

### rbegin

```cpp
reverse_iterator rbegin() noexcept
```

返回反向迭代器（最后一个元素）。

```cpp
const_reverse_iterator rbegin() const noexcept
```

返回反向只读迭代器（最后一个元素）。

### rend

```cpp
reverse_iterator rend() noexcept
```

返回反向迭代器（第一个元素的前面一个元素）。

```cpp
const_reverse_iterator rend() const noexcept
```

返回反向只读迭代器（第一个元素的前面一个元素）

### cbegin

```cpp
const_iterator cbegin() const noexcept
```

begin 的常量版本。

### cend

```cpp
const_iterator cend() const noexcept
```

end 的常量版本。

### crbegin

```cpp
const_reverse_iterator crbegin() const noexcept
```

rbegin 的常量版本、

### crend

```cpp
const_reverse_iterator crend() const noexcept
```

rend 的常量版本。

### size

```cpp
size_type size() const noexcept
```

返回 vector 已存储的元素长度。

### max_size

返回 vector 最大能够存储的长度。

```cpp
size_type max_size() const noexcept
```

### capacity

```cpp
size_type capacity() const noexcept
```

返回 vector 在不扩容的情况下最多能够存储的最大元素数量。

### at

```cpp
_Ty& at(const size_type _Pos)
```

返回指定下标上的元素。（有越界检查）

```cpp
const _Ty& at(const size_type _Pos) const
```

返回指定下标上的元素（常量引用）。（有越界检查）

### front

```cpp
_Ty& front() noexcept
```

返回第一个元素的引用。

```cpp
const _Ty& front() const noexcept
```

返回第一个元素的常量引用。

### back

```cpp
_Ty& back() noexcept
```

返回最后一个元素的引用。

```cpp
const _Ty& back() const noexcept
```

返回最后一个元素的常量引用。

### get_allocator

```cpp
allocator_type get_allocator() const noexcept
```

获取内存分配器。

## 重载运算符

### operator=

```cpp
vector& operator=(vector&& _Right) noexcept(_Choose_pocma_v<_Alty> != _Pocma_values::_No_propagate_allocators)
```

vector 之间的赋值。

```cpp
vector& operator=(initializer_list<_Ty> _Ilist)
```

将 vector 赋值为列表。

### operator\[\]

```cpp
_Ty& operator[](const size_type _Pos) noexcept
```

返回指定下标上的元素。（没有越界检查）

```cpp
const _Ty& operator[](const size_type _Pos) const noexcept
```

返回指定下标上的元素（常量引用）。（没有越界检查）

## 非成员函数

### swap

```cpp
void swap(vector<_Ty, _Alloc>& _Left, vector<_Ty, _Alloc>& _Right) noexcept
```

交换两个 vector。

## 非成员重载运算符

### operator==

```cpp
bool operator==(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回两个 vector 是否相等。

### operator!=

```cpp
bool operator!=(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回两个 vector 是否不相等、

### operator<

```cpp
bool operator<(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回第一个 vector 是否小于第二个 vector。

### operator>

```cpp
bool operator>(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回第一个 vector 是否大于第二个 vector。

### operator<=

```cpp
bool operator<=(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回第一个 vector 是否小于等于第二个 vector。

### operator>=

```cpp
bool operator>=(const vector<_Ty, _Alloc>& _Left, const vector<_Ty, _Alloc>& _Right)
```

返回第一个 vector 是否大于等于第二个 vector。