# swap (非メンバ関数)
* array[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class T, size_t N>
  void swap(array<T, N>& x, array<T, N>& y)
                 noexcept(noexcept(x.swap(y))); // C++11

  template <class T, size_t N>
  constexpr void swap(array<T, N>& x, array<T, N>& y)
                 noexcept(noexcept(x.swap(y))); // C++20
}
```
* x.swap[link swap.md]

## 概要
2つのarrayオブジェクトを入れ替える。


## 効果
`x.`[`swap`](swap.md)`(y);`


## 戻り値
なし


## 例外
`x.`[`swap`](swap.md)`(y)`が例外を投げない場合、この関数は決して例外を投げない。


## 例
```cpp example
#include <iostream>
#include <array>
#include <string>
#include <algorithm>

template <class T, std::size_t N>
void print(const std::string& name, const std::array<T, N>& ar)
{
  std::cout << name << " : {";
  std::for_each(ar.begin(), ar.end(), [](const T& x) { std::cout << x << " "; });
  std::cout << "}" << std::endl;
}

int main ()
{
  std::array<int, 3> x = {4, 5, 6};
  std::array<int, 3> y = {1, 2, 3};

  std::swap(x, y);

  print("x", x);
  print("y", y);
}
```
* std::swap[color ff0000]


### 出力
```
x : {1 2 3 }
y : {4 5 6 }
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
- [P1032R1 Misc constexpr bits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1032r1.html)
