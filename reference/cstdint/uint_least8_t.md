# uint_least8_t
* cstdint[meta header]
* std[meta namespace]
* type-alias[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  using uint_least8_t = unsigned-integer-type;
}
```
* unsigned-integer-type[italic]

## 概要
8ビット以上の、最も小さい符号なし整数型。

[`uint8_t`](uint8_t.md)型が環境によっては定義されないため、そのような状況でこの型を使用する。

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.2 [mark verified]
- [GCC](/implementation.md#gcc): 4.7.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 2010 [mark verified], 2012 [mark verified], 2013 [mark verified]
