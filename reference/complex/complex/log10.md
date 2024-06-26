# log10
* complex[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class T>
  complex<T>
    log10(const complex<T>& x); // (1) C++03
  template <class T>
  constexpr complex<T>
    log10(const complex<T>& x); // (1) C++26
}
```

## 概要
複素数の常用対数（10 を底とした対数）を得る。log は logarithm（対数）、あるいは、logarithmic function（対数関数）の略。


## 戻り値
引数 `x` の常用対数（10 を底とした対数）。[`log`](log.md)`(x) /` [`log`](log.md)`(10)` で定義される。


## 備考
- 分岐截断は負の実軸に沿っている。
- C99 の規格（および C11 の規格）では、本関数と等価と思われる関数名群 `clog10`、`clog10f`、`clog10l` が future library directions として予約されているが、これらの関数の挙動については（名前から明らかであるものの）一切記載はない。
- 常用対数の算出については、一部の算術型、および、[`valarray`](/reference/valarray.md) クラステンプレートに対しても、他のヘッダで定義されている。

	| 引数の型                                  | 関数                                             | ヘッダ                               | 備考       |
	|-------------------------------------------|--------------------------------------------------|--------------------------------------|------------|
	| `float`                                   | [`log10`](/reference/cmath/log10.md)             | [`cmath`](/reference/cmath.md)       |            |
	| `double`                                  | [`log10`](/reference/cmath/log10.md)             | [`cmath`](/reference/cmath.md)       |            |
	| `long double`                             | [`log10`](/reference/cmath/log10.md)             | [`cmath`](/reference/cmath.md)       |            |
	| 任意の整数型                              | [`log10`](/reference/cmath/log10.md)             | [`cmath`](/reference/cmath.md)       | C++11 から |
	| [`valarray`](/reference/valarray.md)`<T>` | [`log10`](/reference/valarray/valarray/log10.md) | [`valarray`](/reference/valarray.md) |            |


## 例
```cpp example
#include <iostream>
#include <complex>

int main()
{
  std::complex<double> c(1.0, 2.0);

  std::complex<double> result = std::log10(c);
  std::cout << "log10( " << c << " ) = " << result << std::endl;
}
```
* std::log10[color ff0000]

### 出力
```
log10( (1,2) ) = (0.349485,0.480829)
```


## バージョン
### 言語
- C++98

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified]
- [GCC](/implementation.md#gcc): 4.3.6 [mark verified], 4.4.7 [mark verified], 4.5.4 [mark verified], 4.6.4 [mark verified], 4.7.3 [mark verified], 4.8.1 [mark verified], 4.8.2 [mark verified], 4.9.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 関連項目
| 名前                                 | 説明                                      |
|--------------------------------------|-------------------------------------------|
| [`acos`](acos.md)                    | 複素数の逆余弦を求める。                  |
| [`asin`](asin.md)                    | 複素数の逆正弦を求める。                  |
| [`atan`](atan.md)                    | 複素数の逆正接を求める。                  |
| [`acosh`](acosh.md)                  | 複素数の双曲線逆余弦を求める。            |
| [`asinh`](asinh.md)                  | 複素数の双曲線逆正弦を求める。            |
| [`atanh`](atanh.md)                  | 複素数の双曲線逆正接を求める。            |
| [`cos`](cos.md)                      | 複素数の余弦を求める。                    |
| [`cosh`](cosh.md)                    | 複素数の双曲線余弦を求める。              |
| [`exp`](exp.md)                      | 自然対数の底 e の累乗（複素数）を求める。 |
| [`log`](log.md)                      | 複素数の自然対数を求める。                |
| [`pow`](pow.md)                      | 複素数の累乗を求める。                    |
| [`sin`](sin.md)                      | 複素数の正弦を求める。                    |
| [`sinh`](sinh.md)                    | 複素数の双曲線正弦を求める。              |
| [`sqrt`](sqrt.md)                    | 複素数の平方根を求める。                  |
| [`tan`](tan.md)                      | 複素数の正接を求める。                    |
| [`tanh`](tanh.md)                    | 複素数の双曲線正接を求める。              |
| [`log10`](/reference/cmath/log10.md) | 実数の常用対数を求める。                  |


## 参照
- [P1383R2 More constexpr for `<cmath>` and `<complex>`](https://open-std.org/jtc1/sc22/wg21/docs/papers/2023/p1383r2.pdf)
    - C++26で`constexpr`対応した
