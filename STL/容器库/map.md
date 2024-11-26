## 定义

```cpp
template <class _Kty, 
          class _Ty, 
          class _Pr = less<_Kty>, 
          class _Alloc = allocator<pair<const _Kty, _Ty>>>
class map
```

## 成员类型

### key_type

```cpp
using key_type = _Kty;
```

键类型。

### mapped_type

```cpp
using mapped_type = _Ty;
```

映射类型。

### key_compare

```cpp
using key_compare = _Pr;
```

键比较器。

### value_compare

```cpp
using value_compare = typename _Mybase::value_compare;
```

值比较器。

### value_type

```cpp
using value_type = pair<const _Kty, _Ty>;
```

键值类型。

### allocator_type

```cpp
using allocator_type = typename _Mybase::allocator_type;
```

内存分配器类型。

### size_type

```cpp
using size_type = typename _Mybase::size_type;
```

长度类型。

### difference_type

```cpp
using difference_type = typename _Mybase::difference_type;
```

差异类型。

### pointer

```cpp
using pointer = typename _Mybase::pointer;
```

指针类型。

### const_pointer

```cpp
using const_pointer = typename _Mybase::const_pointer;
```

常量指针类型。

### reference

```cpp
using reference = value_type&;
```

引用类型。

### const_reference

```cpp
using const_reference = const value_type&;
```

常量引用类型。

### iterator

```cpp
using iterator = typename _Mybase::iterator;
```

迭代器类型。

### const_iterator

```cpp
using const_iterator = typename _Mybase::const_iterator;
```

常量迭代器类型。

### reverse_iterator

```cpp
using reverse_iterator = typename _Mybase::reverse_iterator;
```

反向迭代器类型。

### const_reverse_iterator

```cpp
using const_reverse_iterator = typename _Mybase::const_reverse_iterator;
```

常量反向迭代器。

## 成员函数

### 构造函数

```cpp
map()
```

构造空的 map。

```cpp
explicit map(const allocator_type& _Al)
```

使用指定内存分配器构造 map。

```cpp
map(const map& _Right)
```

拷贝另一个 map 构造 map。

```cpp
map(const map& _Right, const allocator_type& _Al)
```

拷贝另一个 map，并使用指定内存分配器构造 map。

```cpp
explicit map(const key_compare& _Pred)
```

使用指定键比较器构造 map。

```cpp
map(const key_compare& _Pred, const allocator_type& _Al)
```

使用指定的键比较器和内存分配器构造 map。

```cpp
map(_Iter _First, _Iter _Last)
```

使用一个迭代器区间内的元素构造 map。

```cpp
map(_Iter _First, _Iter _Last, const key_compare& _Pred)
```

使用一个迭代器区间内的元素和指定的键比较器构造 map。

```cpp
map(_Iter _First, _Iter _Last, const allocator_type& _Al)
```

使用一个迭代器区间内的元素和指定的内存分配器构造 map。

```cpp
map(_Iter _First, _Iter _Last, const key_compare& _Pred, const allocator_type& _Al)
```

使用一个迭代器区间内的元素、指定的键比较器以及内存分配器构造 map。

```cpp
map(map&& _Right)
```

使用另一个右值 map 构造 map。

```cpp
map(map&& _Right, const allocator_type& _Al)
```

使用另一个右值 map 和指定内存分配器构造 map。

```cpp
map(initializer_list<value_type> _Ilist)
```

用列表初始化 map。

```cpp
map(initializer_list<value_type> _Ilist, const key_compare& _Pred)
```

以列表和键比较器初始化 map。

```cpp
map(initializer_list<value_type> _Ilist, const allocator_type& _Al)
```

以列表和内存分配器初始化 map。

```cpp
map(initializer_list<value_type> _Ilist, const key_compare& _Pred, const allocator_type& _Al)
```

以列表、键比较器和内存分配器初始化 map。

### swap

```cpp
void swap(map& _Right) noexcept(noexcept(_Mybase::swap(_Right)))
```

与另一个 map 交换。

### insert

```cpp
pair<iterator, bool> insert(_Valty&& _Val)
```

插入元素到 map 中。

```cpp
iterator insert(const_iterator _Where, _Valty&& _Val)
```

插入元素到尽可能接近指定位置的地方。

### try_emplace

```cpp
pair<iterator, bool> try_emplace(const key_type& _Keyval, _Mappedty&&... _Mapval)
```

尝试构造并插入元素，如果键已存在则取消。

```cpp
iterator try_emplace(const const_iterator _Hint, const key_type& _Keyval, _Mappedty&&... _Mapval)
```

在尽可能靠近指定位置的地方尝试构造并插入元素，如果键已存在则取消。

```cpp
pair<iterator, bool> try_emplace(key_type&& _Keyval, _Mappedty&&... _Mapval)
```

尝试构造并插入元素，如果键已存在则取消。（右值引用）

```cpp
iterator try_emplace(const const_iterator _Hint, key_type&& _Keyval, _Mappedty&&... _Mapval)
```

在尽可能靠近指定位置的地方尝试构造并插入元素，如果键已存在则取消。（右值引用）

### insert_or_assign

```cpp
pair<iterator, bool> insert_or_assign(const key_type& _Keyval, _Mappedty&& _Mapval)
```

插入元素，如果键已存在则覆盖值。

```cpp
iterator insert_or_assign(const const_iterator _Hint, const key_type& _Keyval, _Mappedty&& _Mapval)
```

插入元素在尽量靠近指定位置的地方，如果键已存在则覆盖值。

```cpp
pair<iterator, bool> insert_or_assign(key_type&& _Keyval, _Mappedty&& _Mapval)
```

插入元素，如果键已存在则覆盖值。（右值引用）

```cpp
iterator insert_or_assign(const const_iterator _Hint, key_type&& _Keyval, _Mappedty&& _Mapval)
```

插入元素在尽量靠近指定位置的地方，如果键已存在则覆盖值。（右值引用）

### at

```cpp
mapped_type& at(const key_type& _Keyval)
```

返回键对应值的引用，没找到则抛异常。

```cpp
const mapped_type& at(const key_type& _Keyval) const
```

返回键对应值的常量引用，没找到则抛异常。

### count

```cpp
size_type count(const key_type& _Keyval) const
```

返回对应键的数量。

```cpp
size_type count(const _Other& _Keyval) const
```

返回与参数匹配的键值的数量。

### lower_bound

```cpp
iterator lower_bound(const key_type& _Keyval)
```

返回第一个大于等于键的对应迭代器。

```cpp
const_iterator lower_bound(const key_type& _Keyval) const
```

返回第一个大于等于键的对应常量迭代器。

```cpp
iterator lower_bound(const _Other& _Keyval)
```

返回第一个大于等于给定参数的键的迭代器。

```cpp
const_iterator lower_bound(const _Other& _Keyval) const
```

返回第一个大于等于给定参数的键的常量迭代器。

### upper_bound

```cpp
iterator upper_bound(const key_type& _Keyval)
```

返回第一个大于键的对应迭代器。

```cpp
const_iterator upper_bound(const key_type& _Keyval) const
```

返回第一个大于键的对应常量迭代器。

```cpp
iterator upper_bound(const _Other& _Keyval)
```

返回第一个大于给定参数的键的迭代器。

```cpp
const_iterator upper_bound(const _Other& _Keyval) const
```

返回第一个大于给定参数的键的常量迭代器。

### equal_range

```cpp
pair<iterator, iterator> equal_range(const key_type& _Keyval)
```

返回匹配对应键的迭代器范围。

```cpp
pair<const_iterator, const_iterator> equal_range(const key_type& _Keyval) const
```

返回匹配对应键的常量迭代器范围。

```cpp
pair<iterator, iterator> equal_range(const _Other& _Keyval)
```

返回与参数匹配的键的迭代器范围。

```cpp
pair<const_iterator, const_iterator> equal_range(const _Other& _Keyval) const
```

返回与参数匹配的键的常量迭代器范围。

### clear

```cpp
void clear() noexcept
```

清空 map。

### erase

```cpp
iterator erase(iterator _Where) noexcept
```

删除迭代器位置的元素。

```cpp
iterator erase(const_iterator _Where) noexcept
```

删除常量迭代器位置的元素。

```cpp
iterator erase(const_iterator _First, const_iterator _Last) noexcept
```

删除指定常量迭代器范围内的元素。

```cpp
size_type erase(const key_type& _Keyval) noexcept(noexcept(_Eqrange(_Keyval)))
```

删除所有匹配键的元素。

### find

```cpp
iterator find(const key_type& _Keyval)
```

返回第一个匹配键的元素的迭代器。

```cpp
const_iterator find(const key_type& _Keyval) const
```

返回第一个匹配键的元素的常量迭代器。

```cpp
iterator find(const _Other& _Keyval)
```

返回与参数匹配的键的第一个元素的迭代器。

```cpp
const_iterator find(const _Other& _Keyval) const
```

返回与参数匹配的键的第一个元素的常量迭代器。

### begin

```cpp
iterator begin() noexcept
```

返回第一个元素的迭代器。

```cpp
const_iterator begin() const noexcept
```

返回第一个元素的常量迭代器。

### end

```cpp
iterator end() noexcept
```

返回最后一个元素的前面一个元素的迭代器。

```cpp
const_iterator end() const noexcept
```

返回最后一个元素的前面一个元素的常量迭代器。

### rbegin

```cpp
reverse_iterator rbegin() noexcept
```

返回最后一个元素的反向迭代器。

```cpp
const_reverse_iterator rbegin() const noexcept
```

返回最后一个元素的常量反向迭代器。

### rend

```cpp
reverse_iterator rend() noexcept
```

返回第一个元素的前面一个元素的反向迭代器。

```cpp
const_reverse_iterator rend() const noexcept
```

返回第一个元素的前面一个元素的常量反向迭代器。

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

rbegin 的常量版本。

### crend

```cpp
const_reverse_iterator crend() const noexcept
```

rend 的常量版本。

### size

```cpp
size_type size() const noexcept
```

返回 map 存储的元素的数量。

### max_size

```cpp
size_type max_size() const noexcept
```

返回最大能够存储的元素的数量。

### empty

```cpp
bool empty() const noexcept
```

返回 map 是否是空的。

### get_allocator

```cpp
allocator_type get_allocator() const noexcept
```

返回内存分配器。

### key_comp

```cpp
key_compare key_comp() const
```

返回键比较器。

### value_comp 

```cpp
value_compare value_comp() const
```

返回值比较器。

## 重载运算符

### operator=

```cpp
map& operator=(const map& _Right)
```

将另一个右值内的元素拷贝到当前 map。

```cpp
map& operator=(initializer_list<value_type> _Ilist)
```

将 map 赋值为列表。

### operator\[\]

```cpp
mapped_type& operator[](const key_type& _Keyval)
```

返回键对应的值的引用，如果没找到则初始化一个。

```cpp
mapped_type& operator[](key_type&& _Keyval)
```

返回键（右值引用）对应的值的引用，如果没找到则初始化一个。

## 非成员函数

### swap

```cpp
swap(map<_Kty, _Ty, _Pr, _Alloc>& _Left, map<_Kty, _Ty, _Pr, _Alloc>& _Right) noexcept(noexcept(_Left.swap(_Right)))
```

交换两个 map。

## 非成员重载运算符

### operator==

```cpp
bool operator==(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```

判断两个 map 是否相等。

### operator!=

```cpp
bool operator!=(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```

判断两个 map 是否不相等。

```cpp
bool operator<(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```

返回是否小于。

### operator>

```cpp
bool operator>(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```

返回是否大于。

### operator<=

```cpp
bool operator<=(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```

返回是否小于等于。

### operator>=

```cpp
bool operator>=(const map<_Kty, _Ty, _Pr, _Alloc>& _Left, const map<_Kty, _Ty, _Pr, _Alloc>& _Right)
```