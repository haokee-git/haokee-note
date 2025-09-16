deque，双端队列是有索引的序列容器。不同于 [[vector]] 存储在一个大块中，deque 采用单独分配的固定尺寸数组，因此它拥有较大的最小内存开销。

## 定义

```cpp
template <class _Ty, 
          class _Alloc = allocator<_Ty>>
class deque  // In namespace std
```

## 成员类型

### allocator_type

```cpp
using allocator_type  = _Alloc;
```

内存分配器类型。

### value_type

```cpp
using value_type = _Ty;
```

值类型。

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

### iterator

```cpp
using iterator = _Deque_iterator<_Scary_val>;
```

迭代器类型。

### const_iterator

```cpp
using const_iterator = _Deque_const_iterator<_Scary_val>;
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

常量反向迭代器类型。

## 成员函数

### 构造函数

```cpp
deque()
```

构造空的 deque。

```cpp
explicit deque(const _Alloc& _Al)
```

由指定内存分配器构造空的 deque。

```cpp
explicit deque(_CRT_GUARDOVERFLOW size_type _Count, const _Alloc& _Al = _Alloc())
```

给定初始元素数量以及指定内存分配器，构造 deque。

```cpp
deque(_CRT_GUARDOVERFLOW size_type _Count, const _Ty& _Val)
```

指定初始元素数量以及指定初始元素，构造 deque。

```cpp
deque(_CRT_GUARDOVERFLOW size_type _Count, const _Ty& _Val, const _Alloc& _Al)
```

指定初始元素数量、初始元素以及内存分配器，构造 deque。

```cpp
deque(_Iter _First, _Iter _Last)
```

使用左闭右开迭代器区间构造 deque。

```cpp
deque(_Iter _First, _Iter _Last, const _Alloc& _Al)
```

指定迭代器区间与内存分配器构造 deque。

```cpp
deque(const deque& _Right)
```

用另一个 deque 构造 deque。

```cpp
deque(const deque& _Right, const _Identity_t<_Alloc>& _Al)
```

指定另一个 deque 以及内存分配器，构造 deque。

```cpp
deque(deque&& _Right)
```

用另一个 deque 构造 deque（右值引用）。

```cpp
deque(deque&& _Right, const _Identity_t<_Alloc>& _Al)
```

用另一个 deque（右值引用）及内存分配器构造 deque。

```cpp
deque(initializer_list<_Ty> _Ilist, const _Alloc& _Al = allocator_type())
```

给定列表和内存分配器，构造 deque。

### 析构函数

```cpp
~deque()
```

析构一个 deque。

### assign

```cpp
void assign(initializer_list<_Ty> _Ilist)
```

复制列表中的元素到 deque。

```cpp
void assign(_Iter _First, _Iter _Last)
```

复制迭代器区间内的元素到 deque。

```cpp
void assign(_CRT_GUARDOVERFLOW size_type _Count, const _Ty& _Val)
```

给定元素数量与元素值，赋值到 deque。

### get_allocator

```cpp
_NODISCARD allocator_type get_allocator() const noexcept
```

获取内存分配器。

### begin

```cpp
_NODISCARD iterator begin() noexcept
```

获取第一个元素的迭代器。

```cpp
_NODISCARD const_iterator begin() const noexcept
```

获取第一个元素的常量迭代器。

### end

```cpp
_NODISCARD iterator end() noexcept
```

获取最后一个元素的后面一个元素的迭代器。

```cpp
_NODISCARD const_iterator end() const noexcept
```

获取最后一个元素的后面一个元素的常量迭代器。

### rbegin

```cpp
_NODISCARD reverse_iterator rbegin() noexcept
```

获取最后一个元素的反向迭代器。

```cpp
_NODISCARD const_reverse_iterator rbegin() const noexcept
```

获取最后一个元素的常量反向迭代器。

### rend

```cpp
_NODISCARD reverse_iterator rend() noexcept
```

获取第一个元素的前面一个元素的反向迭代器。

```cpp
_NODISCARD const_reverse_iterator rend() const noexcept
```

获取第一个元素的前面一个元素的常量反向迭代器。

### cbegin

```cpp
_NODISCARD const_iterator cbegin() const noexcept
```

begin 的常量版本。

### rend

```cpp
_NODISCARD const_iterator cend() const noexcept
```

end 的常量版本。

### crbegin

```cpp
_NODISCARD const_reverse_iterator crbegin() const noexcept
```

rbegin 的常量版本。

### crend

```cpp
_NODISCARD const_reverse_iterator crend() const noexcept
```

rend 的常量版本。

### empty

```cpp
_NODISCARD_EMPTY_MEMBER bool empty() const noexcept
```

判断 deque 是否为空。

### size

```cpp
_NODISCARD size_type size() const noexcept
```

获取 deque 当前存储的元素数量。

### max_size

```cpp
_NODISCARD size_type max_size() const noexcept
```

获取 deque 最多能够存储的元素数量。

### resize

```cpp
void resize(_CRT_GUARDOVERFLOW size_type _Newsize)
```

初始化为指定元素数量的 deque。

```cpp
resize(_CRT_GUARDOVERFLOW size_type _Newsize, const _Ty& _Val)
```

指定元素数量以及元素值，初始化 deque。

### shrink_to_fit

```cpp
void shrink_to_fit()
```

释放多余的内存。

### at

```cpp
_NODISCARD const_reference at(size_type _Pos) const
```

获取指定位置上的元素的引用。（带越界判断）

```cpp
_NODISCARD reference at(size_type _Pos)
```

获取指定位置上的元素的常量引用。（带越界判断）

### front

```cpp
_NODISCARD reference front() noexcept
```

获取第一个元素的引用。

```cpp
_NODISCARD const_reference front() const noexcept
```

获取第一个元素的常量引用。

### back

```cpp
_NODISCARD reference back() noexcept
```

获取最后一个元素的引用。

```cpp
_NODISCARD const_reference back() const noexcept
```

获取最后一个元素的常量引用。

### emplace_front

```cpp
decltype(auto) emplace_front(_Valty&&... _Val)
```

以构造方式在前端插入元素。

### emplace_back

```cpp
decltype(auto) emplace_back(_Valty&&... _Val)
```

以构造方式在后端插入元素。

### emplace

```cpp
iterator emplace(const_iterator _Where, _Valty&&... _Val)
```

在指定位置以构造形式插入元素。

### push_front

```cpp
void push_front(const _Ty& _Val)
```

以赋值方式在前端插入元素。

```cpp
void push_front(_Ty&& _Val)
```

以赋值方式在前端插入元素。（右值引用）

### push_back

```cpp
void push_back(const _Ty& _Val)
```

以赋值方式在后端插入元素。

```cpp
void push_back(_Ty&& _Val)
```

以赋值方式在后端插入元素。（右值引用）

### insert

```cpp
iterator insert(const_iterator _Where, const _Ty& _Val)
```

在指定位置上插入元素。

```cpp
iterator insert(const_iterator _Where, _Ty&& _Val)
```

在指定位置上插入元素。（右值引用）

```cpp
iterator insert(const_iterator _Where, _CRT_GUARDOVERFLOW size_type _Count, const _Ty& _Val)
```

在指定位置上插入指定数量的元素。

```cpp
iterator insert(const_iterator _Where, _Iter _First, _Iter _Last)
```

在指定位置上插入一个迭代器区间内的元素。

```cpp
iterator insert(const_iterator _Where, initializer_list<_Ty> _Ilist)
```

在指定位置上插入列表。

### pop_front

```cpp
void pop_front() noexcept
```

弹出第一个元素。

### pop_back

```cpp
void pop_back() noexcept
```

弹出最后一个元素。

### erase

```cpp
iterator erase(const_iterator _Where) noexcept(is_nothrow_move_assignable_v<value_type>)
```

删除指定位置上的元素。

```cpp
iterator erase(const_iterator _First_arg, const_iterator _Last_arg) noexcept(is_nothrow_move_assignable_v<value_type>)
```

删除指定区间内的元素。

### clear

```cpp
void clear() noexcept
```

清空 deque。

### swap

```cpp
void swap(deque& _Right) noexcept
```

与另一个 deque 交换。

## 重载运算符

### operator=

```cpp
deque& operator=(const deque& _Right)
```

给定另一个 deque 对当前 deque 进行赋值。

```cpp
deque& operator=(deque&& _Right) noexcept(_Alty_traits::is_always_equal::value)
```

给定另一个 deque（右值引用）对当前 deque 进行赋值。

```cpp
deque& operator=(initializer_list<_Ty> _Ilist)
```

将 deque 赋值为列表。

### operator\[\]

```cpp
_NODISCARD reference operator[](size_type _Pos) noexcept
```

获取指定位置上的元素的引用。（不带越界判断）

```cpp
_NODISCARD const_reference operator[](size_type _Pos) const noexcept
```

获取指定位置上的元素的常量引用。（不带越界判断）

## 非成员函数

```cpp
void swap(deque<_Ty, _Alloc>& _Left, deque<_Ty, _Alloc>& _Right) noexcept
```

两个 deque 交换。

## 非成员重载运算符

### operator==

```cpp
_NODISCARD bool operator==(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断两个 deque 是否相等。

### operator!=

```cpp
_NODISCARD bool operator!=(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断两个 deque 是否不相等。

### operator<

```cpp
_NODISCARD bool operator<(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断是否小于。

### operator<=

```cpp
_NODISCARD bool operator<=(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断是否小于等于。

### operator>

```cpp
_NODISCARD bool operator>(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断是是否大于。

### operator>=

```cpp
_NODISCARD bool operator>=(const deque<_Ty, _Alloc>& _Left, const deque<_Ty, _Alloc>& _Right)
```

判断是否大于等于。