# shrink_to_fit
* string[meta header]
* std[meta namespace]
* basic_string[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
void shrink_to_fit();           // (1) C++11
constexpr void shrink_to_fit(); // (1) C++20
```

## 概要
領域をコンテナのサイズまで切り詰める


## 効果
- [`capacity`](capacity.md)`()`を[`size`](size.md)`()`に縮小させるリクエストを行う。
    - 実装依存の最適化を許可するために、縮小するという動作は仕様上強制されない。
- C++17 : この関数によって[`capacity()`](capacity.md)が増えることはない。
- C++17 : [`capacity()`](capacity.md)の縮小が起こる際に、メモリの再割り当てが発生する場合がある。その際、文字列の要素に対する参照、ポインタ、およびイテレータとそれが指す要素への参照は無効となる。


## 戻り値
なし


## 計算量
- C++17 : 最大で、要素数に対して線形時間


## 例
```cpp example
#include <iostream>
#include <string>

int main()
{
  std::wstring s = L"The quick brown fox jumps over the lazy dog";

  std::cout << s.capacity() << std::endl;

  // 要素削除 : capacityは減らない
  s.erase(s.begin() + 8, s.end());
  std::cout << s.capacity() << std::endl;

  // 領域を切り詰める
  s.shrink_to_fit();
  std::cout << s.capacity() << std::endl;
}
```
* shrink_to_fit[color ff0000]
* s.capacity()[link capacity.md]
* s.erase[link erase.md]
* s.begin()[link begin.md]
* s.end()[link end.md]

### 出力例
```
47
47
15
```

## 実装例
```cpp
void basic_string::shrink_to_fit() {
  swap(basic_string(*this));
}
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.4 [mark verified]
- [GCC](/implementation.md#gcc): 4.5.4 [mark verified], 4.6.4 [mark verified], 4.7.3 [mark verified], 4.8.2 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 2010 [mark verified], 2012 [mark verified]


## 関連項目
- [`std::vector<>::shrink_to_fit`](../../vector/vector/shrink_to_fit.md)
- [`std::deque<>::shrink_to_fit`](../../deque/deque/shrink_to_fit.md)


## 参照
- 『[Effective STL - STLを効果的に使いこなす50の鉄則](https://www.amazon.co.jp/dp/4894714108)』 第17項 余分な容量を取り除くには「swap技法」を使おう
- [LWG Issue 755. `std::vector` and `std:string` lack explicit shrink-to-fit operations]
- [LWG Issue 2223. `shrink_to_fit` effect on iterator validity](https://wg21.cmeerw.net/lwg/issue2223)
- [P0980R1 Making `std::string` constexpr](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p0980r1.pdf)
