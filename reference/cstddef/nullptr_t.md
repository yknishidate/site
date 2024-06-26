# nullptr_t
* cstddef[meta header]
* std[meta namespace]
* type-alias[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  using nullptr_t = decltype(nullptr);
}
```

## 概要
ヌルポインタを表すポインタリテラル`nullptr`の型。

## 例
```cpp example
#include <iostream>
#include <type_traits>

int main()
{
  std::cout << "sizeof(nullptr_t): " << sizeof(std::nullptr_t) << std::endl; // sizeof(void*)と同サイズ

  std::cout << "is_object<nullptr_t>: " << std::is_object<std::nullptr_t>::value << std::endl;
  std::cout << "is_scalar<nullptr_t>: " << std::is_scalar<std::nullptr_t>::value << std::endl; // 0 on VS 2010～2012
  std::cout << "is_union<nullptr_t>: " << std::is_union<std::nullptr_t>::value << std::endl;
  std::cout << "is_array<nullptr_t>: " << std::is_array<std::nullptr_t>::value << std::endl;
  std::cout << "is_class<nullptr_t>: " << std::is_class<std::nullptr_t>::value << std::endl;
}
```
* std::nullptr_t[color ff0000]
* std::is_object[link /reference/type_traits/is_object.md]
* std::is_scalar[link /reference/type_traits/is_scalar.md]
* std::is_union[link /reference/type_traits/is_union.md]
* std::is_array[link /reference/type_traits/is_array.md]
* std::is_class[link /reference/type_traits/is_class.md]

### 出力例
```
sizeof(nullptr_t): 8
is_object<nullptr_t>: 1
is_scalar<nullptr_t>: 1
is_union<nullptr_t>: 0
is_array<nullptr_t>: 0
is_class<nullptr_t>: 0
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.1 [mark verified]
- [GCC](/implementation.md#gcc): 4.6.4 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 2010 [mark verified], 2012 [mark verified], 2013 [mark verified]
	- 2010, 2012では[`is_scalar`](../type_traits/is_scalar.md)`<nullptr_t>`が`false_type`（からの派生クラス）となっているバグがある。


## 関連項目
- [C++11 `nullptr`](/lang/cpp11/nullptr.md)
