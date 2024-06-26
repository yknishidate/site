# rbegin
* array[meta header]
* std[meta namespace]
* array[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
reverse_iterator rbegin() noexcept;                       // (1) C++11
constexpr reverse_iterator rbegin() noexcept;             // (1) C++17

const_reverse_iterator rbegin() const noexcept;           // (2) C++11
constexpr const_reverse_iterator rbegin() const noexcept; // (2) C++17
```

## 概要
末尾要素を指す逆イテレータを取得する。


## 戻り値
非`const`な文脈では`reverse_iterator`型で末尾要素への逆イテレータを返し、
`const`な文脈では`const_reverse_iterator`型で末尾要素への逆イテレータを返す。


## 例外
投げない


## 計算量
定数時間


## 例
```cpp example
#include <iostream>
#include <array>

int main()
{
  std::array<int, 3> ar = {1, 2, 3};
  const std::array<int, 3>& car = ar;

  decltype(ar)::reverse_iterator i = ar.rbegin();
  decltype(ar)::const_reverse_iterator ci = car.rbegin();

  std::cout << *i << std::endl;
  std::cout << *ci << std::endl;
}
```
* rbegin[color ff0000]


### 出力
```
3
3
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 4.7.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 2008 (std::tr1) [mark verified], 2010 [mark verified], 2012 [mark verified], 2013 [mark verified], 2015 [mark verified]


## 参照
- [P0031R0 A Proposal to Add Constexpr Modifiers to `reverse_iterator`, `move_iterator`, `array` and Range Access](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)
