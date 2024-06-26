# is_const
* type_traits[meta header]
* std[meta namespace]
* class template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class T>
  struct is_const;

  template <class T>
  inline constexpr bool is_const_v = is_const<T>::value; // C++17
}
```

## 概要
型`T`が`const`修飾型か調べる。`const`修飾型は、`const` および `const volatile` を含む。


## 効果
`is_const`は、型`T`が`const`修飾型であるならば[`true_type`](true_type.md)から派生し、そうでなければ[`false_type`](false_type.md)から派生する。


## 備考
参照型は、`const`修飾型でない。


## 例
```cpp example
#include <type_traits>

static_assert(std::is_const<const int>::value == true, "value == true, const int is const-qualified");
static_assert(std::is_same<std::is_const<const int>::value_type, bool>::value, "value_type == bool");
static_assert(std::is_same<std::is_const<const int>::type, std::true_type>::value, "type == true_type");
static_assert(std::is_const<const int>() == true, "is_const<const int>() == true");

static_assert(std::is_const<int>::value == false, "value == false, int is not const-qualified");
static_assert(std::is_same<std::is_const<int>::value_type, bool>::value, "value_type == bool");
static_assert(std::is_same<std::is_const<int>::type, std::false_type>::value, "type == false_type");
static_assert(std::is_const<int>() == false, "is_const<int>() == false");

static_assert(std::is_const<const volatile int>::value == true, "const volatile int is const-qualified");
static_assert(std::is_const<const int&>::value == false, "const int& is not const-qualified");

int main(){}
```
* std::is_const[color ff0000]

### 出力
```
```

## バージョン
### 言語
- C++11

### 処理系
- [GCC](/implementation.md#gcc): 4.3.4 [mark verified], 4.5.3 [mark verified], 4.6.2 [mark verified], 4.7.0 [mark verified]
- [Visual C++](/implementation.md#visual_cpp): 2008 (std::tr1) [mark verified], 2010 [mark verified], 2012 [mark verified], 2013 [mark verified], 2015 [mark verified]

#### 備考
上の例でコンパイラによってはエラーになる。GCC 4.3.4, 4.5.3, Visual C++ 2010 は `integral_constant` が `operator bool()` を持っていないためエラーになる。


## 参照
- [P0006R0 Adopt Type Traits Variable Templates from Library Fundamentals TS for C++17](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)
