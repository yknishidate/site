# コンストラクタ
* regex[meta header]
* std[meta namespace]
* sub_match[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
constexpr sub_match();
```

## 概要
`sub_match` オブジェクトを構築する


## 要件
[`is_default_constructible`](../../type_traits/is_default_constructible.md)`<iterator>::value == true` であること。


## 効果
各メンバ変数（`first`、`second`、`matched`）を値初期化する。


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  std::csub_match s;
  std::cout << std::boolalpha
            << (s.first == nullptr) << std::endl
            << (s.second == nullptr) << std::endl
            << s.matched << std::endl;
}
```
* csub_match[color ff0000]

### 出力
```
true
true
false
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
