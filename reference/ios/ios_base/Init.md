# Init
* ios[meta header]
* class[meta id-type]
* std[meta namespace]
* ios_base[meta class]

```cpp
namespace std {
  class ios_base::Init {
  public:
    Init();
    ~Init();
  };
}
```

## 概要
`ios_base::Init` は、[`<iostream>`](../../iostream.md) ヘッダで宣言されている 8 つの標準入出力ストリームを適切に構築するためのクラスである。

[`<iostream>`](../../iostream.md) ヘッダをインクルードしている翻訳単位は、[`<iostream>`](../../iostream.md) ヘッダで静的ストレージの `ios_base::Init` 型オブジェクトが定義されているかのように振る舞う。


## メンバ関数

### 構築・破棄
| 名前                                      | 説明           | 対応バージョン |
|-------------------------------------------|----------------|----------------|
| [`(constructor)`](Init/op_constructor.md) | コンストラクタ |                |
| [`(destructor)`](Init/op_destructor.md)   | デストラクタ   |                |


## バージョン
## 言語
- C++98

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5.0 [mark verified], 3.6.0 [mark verified], 3.7.0 [mark verified], 3.8.0 [mark verified]
- [GCC](/implementation.md#gcc): 4.3.6 [mark verified], 4.4.7 [mark verified], 4.5.4 [mark verified], 4.6.4 [mark verified], 4.7.3 [mark verified], 4.8.1 [mark verified], 4.8.2 [mark verified], 4.9.0 [mark verified], 4.9.1 [mark verified], 4.9.2 [mark verified], 5.1.0 [mark verified], 5.2.0 [mark verified], 6.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 参照
- [`cin`](../../iostream/cin.md)
- [`cout`](../../iostream/cout.md)
- [`cerr`](../../iostream/cerr.md)
- [`clog`](../../iostream/clog.md)
- [`wcin`](../../iostream/wcin.md.nolink)
- [`wcout`](../../iostream/wcout.md.nolink)
- [`wcerr`](../../iostream/wcerr.md.nolink)
- [`wclog`](../../iostream/wclog.md.nolink)
