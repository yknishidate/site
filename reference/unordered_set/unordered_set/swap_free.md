# swap (非メンバ関数)
* unordered_set[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class Key, class Hash, class Pred, class Alloc>
  void swap(unordered_set<Key, Hash, Pred, Alloc>& x,
            unordered_set<Key, Hash, Pred, Alloc>& y);

  template <class Key, class Hash, class Pred, class Alloc>
  void swap(unordered_set<Key, Hash, Pred, Alloc>& x,
            unordered_set<Key, Hash, Pred, Alloc>& y)
    noexcept(noexcept(x.swap(y))); // C++17
}
```

## 概要
2 つの `unordered_set` オブジェクトの内容を入れ替える。


## 効果
`x.`[`swap`](swap.md)`(y)` と等価。


## 戻り値
なし


## 例
```cpp example
#include <iostream>
#include <string>
#include <unordered_set>
#include <iterator>
#include <algorithm>

template <class C>
void print(const std::string& label, const C& c, std::ostream& os = std::cout)
{
  os << label << ":";
  std::copy(std::begin(c), std::end(c), std::ostream_iterator<typename C::value_type>(os, ", "));
  os << std::endl;
}

int main()
{
  std::unordered_set<int> us1{ 1, 2, 3, };
  std::unordered_set<int> us2{ 4, 5, 6, };

  print("us1 before", us1);
  print("us2 before", us2);
  swap(us1, us2);
  print("us1 after", us1);
  print("us2 after", us2);
}
```
* swap[color ff0000]
* std::ostream[link /reference/ostream/basic_ostream.md]

### 出力
```
us1 before:3, 2, 1,
us2 before:6, 5, 4,
us1 after:6, 5, 4,
us2 after:3, 2, 1,
```

注：[`unordered_set`](/reference/unordered_set/unordered_set.md) は非順序連想コンテナであるため、出力順序は無意味であることに注意


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.1 [mark verified]
- [GCC](/implementation.md#gcc): 4.7.0 [mark verified]
- [ICC](/implementation.md#icc): ?
- [Visual C++](/implementation.md#visual_cpp): ?

## 実装例
```cpp
namespace std {
  template <class Key, class Hash, class Pred, class Alloc>
  void swap(unordered_set<Key, Hash, Pred, Alloc>& x,
            unordered_set<Key, Hash, Pred, Alloc>& y)
  {
    x.swap(y);
  }
}
```
* swap[link swap.md]

## 関連項目

| 名前 | 説明 |
|----------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [`swap`](swap.md) | 内容の交換（メンバ関数） |
| [`operator=`](op_assign.md) | 代入演算子 |
| [`operator==`](op_equal.md) | 等値比較 |
| [`operator!=`](op_not_equal.md) | 非等値比較 |


## 参照
- [N4258 Cleaning-up noexcept in the Library, Rev 3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)
    - `noexcept` 追加の経緯となる提案文書
