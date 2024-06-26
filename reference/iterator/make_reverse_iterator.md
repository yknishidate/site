# make_reverse_iterator
* iterator[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp14[meta cpp]

```cpp
namespace std {
  template <class Iterator>
  reverse_iterator<Iterator>
    make_reverse_iterator(Iterator i); // C++14

  template <class Iterator>
  constexpr reverse_iterator<Iterator>
    make_reverse_iterator(Iterator i); // C++17
}
```
* reverse_iterator[link reverse_iterator.md]

## 概要
`reverse_iterator`オブジェクトを作るヘルパ関数


## 戻り値
```cpp
reverse_iterator<Iterator>(i)
```
* reverse_iterator[link reverse_iterator.md]


## 例
```cpp example
#include <iostream>
#include <iterator>
#include <algorithm>

int main()
{
  int ar[] = {1, 2, 3};

  std::for_each(
    std::make_reverse_iterator(ar + 3),
    std::make_reverse_iterator(ar),
    [](int x) {
      std::cout << x << std::endl;
    }
  );
}
```
* std::make_reverse_iterator[color ff0000]

### 出力
```
3
2
1
```

## バージョン
### 言語
- C++14

### 処理系
- [Clang](/implementation.md#clang): 3.5 [mark verified]
- [GCC](/implementation.md#gcc): 5.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 参照
- [LWG Issue 2285. `make_reverse_iterator`](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-defects.html#2285)
- [P0031R0 A Proposal to Add Constexpr Modifiers to `reverse_iterator`, `move_iterator`, `array` and Range Access](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)
