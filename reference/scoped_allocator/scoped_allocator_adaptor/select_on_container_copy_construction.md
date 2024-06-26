# select_on_container_copy_construction
* scoped_allocator[meta header]
* std[meta namespace]
* scoped_allocator_adaptor[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
scoped_allocator_adaptor select_on_container_copy_construction() const;
```

## 概要
コンテナのコピー構築に必要なアロケータを取得する。


## 戻り値
`scoped_allocator_adaptor`の各アロケータ`A`について、[`allocator_traits`](/reference/memory/allocator_traits.md)`<A>::`[`select_on_container_copy_construction`](/reference/memory/allocator_traits/select_on_container_copy_construction.md)`()`が返すアロケータオブジェクトからなる`scoped_allocator_adaptor`オブジェクトを返す。


## 例
```cpp example
#include <iostream>
#include <vector>
#include <string>

#include <scoped_allocator>

template <class T>
using alloc_t = std::allocator<T>;

// コンテナの要素(Inner)
using string = std::basic_string<
  char,
  std::char_traits<char>,
  alloc_t<char>
>;

// コンテナ(Outer)
template <class T>
using vector = std::vector<
  T,
  std::scoped_allocator_adaptor<alloc_t<T>, alloc_t<typename T::value_type>>
>;

int main()
{
  vector<string>::allocator_type alloc {
    alloc_t<string>(), // vector自体のアロケータオブジェクト
    alloc_t<char>()    // vectorの全ての要素に使用するアロケータオブジェクト
  };

  vector<string>::allocator_type for_copy_alloc = alloc.select_on_container_copy_construction();
}
```
* select_on_container_copy_construction()[color ff0000]

### 出力
```
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.1 [mark verified]
- [GCC](/implementation.md#gcc): 4.7.3 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
