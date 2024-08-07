# scale

* [mathjax enable]
* linalg[meta header]
* function template[meta id-type]
* std::linalg[meta namespace]
* cpp26[meta cpp]


```cpp
namespace std::linalg {
  template<class Scalar,
           inout-object InOutObj>
  void scale(Scalar alpha,
             InOutObj x);            // (1)

  template<class ExecutionPolicy,
           class Scalar,
           inout-object InOutObj>
  void scale(ExecutionPolicy&& exec,
             Scalar alpha,
             InOutObj x);            // (2)
}
```


## 概要
以下のように、ベクトル`x`を`alpha`倍したものを`x`に代入する。

$$
\mathbf{x}\leftarrow\alpha\mathbf{x}
$$


## 適格要件
- (2): [`is_execution_policy`](/reference/execution/is_execution_policy.md)`<ExecutionPolicy>::value`が`true`


## 効果
ベクトル`x`を`alpha`倍する。

- (1): 逐次実行する。
- (2): 指定された実行ポリシーに応じて実行する。


## 戻り値
なし


## 例


### 出力


## バージョン
### 言語
- C++26

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): ??
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 関連項目
- [`execution`](/reference/execution.md)
- [`mdspan`](/reference/mdspan.md)


## 参照
- [P1673R13 A free function linear algebra interface based on the BLAS](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2023/p1673r13.html)
- [`LAPACK: cscal`](https://netlib.org/lapack/explore-html/d2/de8/group__scal_gacce468103c83fa18bae078d5f49fefe2.html#gacce468103c83fa18bae078d5f49fefe2)

