# operator!=
* regex[meta header]
* std[meta namespace]
* regex_token_iterator[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
// operator==により、以下の演算子が使用可能になる (C++20)
bool operator!=(const regex_token_iterator& right) const;
```

## 概要
`regex_token_iterator` の非等値比較を行う。


## 戻り値
`!(*this == right)`


## 備考
- 本メンバ関数が `true` を返したとしても、イテレータの指す文字列が等しくないとは限らないことに注意すること。（下記の例を参照）


## 例
```cpp example
#include <iostream>
#include <iterator>
#include <regex>
#include <string>
#include <initializer_list>

int main()
{
  // 検索対象は 1 番目の列挙子と 2 番目の列挙子が同じ文字列になっている
  const std::string s("enum E { enumerator1 = value1, enumerator1 = value1, enumerator3 = value3, };");
  const std::regex re(R"((\w+)\s*=\s*(\w+))"); // 列挙子とその値をグループ化

  // 同一の引数で 2 つのイテレータを構築する
  std::sregex_token_iterator it1(std::begin(s), std::end(s), re, { 1, 2 });
  std::sregex_token_iterator it2(std::begin(s), std::end(s), re, { 1, 2 });

  std::advance(it2, 2); // 2 つ進める（2 番目の enumerator1 を指す）

  // operator!= で比較する
  std::cout << std::boolalpha << (it1 != it2) << std::endl;

  // 参考のため、各サブマッチの詳細を出力する
  std::cout << "match range = (" << (it1->first - std::begin(s)) << ", " << (it1->second - std::begin(s)) << "), "
               "str = '" << it1->str() << '\'' << std::endl;
  std::cout << "match range = (" << (it2->first - std::begin(s)) << ", " << (it2->second - std::begin(s)) << "), "
               "str = '" << it2->str() << '\'' << std::endl;
}
```
* !=[color ff0000]
* std::regex[link /reference/regex/basic_regex.md]
* std::advance[link /reference/iterator/advance.md]
* str()[link /reference/regex/sub_match/str.md]

### 出力
```
true
match range = (9, 20), str = 'enumerator1'
match range = (31, 42), str = 'enumerator1'
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 関連項目
| 名前                                       | 説明           | 対応バージョン |
|--------------------------------------------|----------------|----------------|
| [`operator*`](op_deref.md)                 | 間接参照       | C++11          |
| [`operator->`](op_arrow.md)                | メンバアクセス | C++11          |
| [`(constructor)`](op_constructor.md) | コンストラクタ | C++11          |
| [`operator++`](op_increment.md)            | インクリメント | C++11          |
| [`operator==`](op_equal.md)                | 等値比較       | C++11          |

## 参照
- [P1614R2 The Mothership has Landed](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1614r2.html)
    - C++20での三方比較演算子の追加と、関連する演算子の自動導出
