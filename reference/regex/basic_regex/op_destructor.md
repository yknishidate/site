# デストラクタ
* regex[meta header]
* std[meta namespace]
* basic_regex[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
~basic_regex();
```


## 概要
正規表現オブジェクトを破棄する。


## 効果
正規表現オブジェクトを破棄する。


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  const char s[] = " abc ";
  std::cout << std::boolalpha;

  const std::regex re("ABC", std::regex_constants::icase);
  std::cout << std::regex_search(s, re) << std::endl;

  // スコープの終わりで破棄される。
}
```
* std::regex_search[link ../regex_search.md]
* std::regex_constants::icase[link ../regex_constants/syntax_option_type.md]

### 出力
```
true
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 4.9.2 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
