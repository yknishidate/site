# operator!=
* regex[meta header]
* std[meta namespace]
* regex_iterator[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
// operator==により、以下の演算子が使用可能になる (C++20)
bool operator!=(const regex_iterator& right) const; // (1) C++11
```

## 概要
`regex_iterator` の非等値比較を行う。


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

int main()
{
  std::regex re("\\d+");
  std::string s("+1-1+1-");

  // 2 つのイテレータを同一引数で生成する
  std::sregex_iterator it1(std::begin(s), std::end(s), re);
  std::sregex_iterator it2(std::begin(s), std::end(s), re);

  // 一方だけ  1 つ進める
  ++it1;

  // operator!= で比較する
  std::cout << std::boolalpha << (it1 != it2) << std::endl;

  // 参考のため、それぞれのマッチ結果の詳細を出力する
  std::cout << "it1:'" << it1->str() << "'(" << ((*it1)[0].first - std::begin(s)) << ", " << ((*it1)[0].second - std::begin(s)) << ')' << std::endl;
  std::cout << "it2:'" << it2->str() << "'(" << ((*it2)[0].first - std::begin(s)) << ", " << ((*it2)[0].second - std::begin(s)) << ')' << std::endl;
}
```
* !=[color ff0000]
* std::regex[link /reference/regex/basic_regex.md]
* str()[link /reference/regex/match_results/str.md]

### 出力
```
true
it1:'1'(3, 4)
it2:'1'(1, 2)
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
| 名前                        | 説明     |
|-----------------------------|----------|
| [`operator==`](op_equal.md) | 等値比較 |


## 参照
- [P1614R2 The Mothership has Landed](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1614r2.html)
    - C++20での三方比較演算子の追加と、関連する演算子の自動導出
