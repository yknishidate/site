# swap
* regex[meta header]
* std[meta namespace]
* match_results[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
void swap(const match_results& that);
```

## 概要
`match_results` オブジェクトの内容を交換する。


## 効果
`*this` の内容と `that` の内容を交換する。


## 計算量
定数時間


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  const char s[] = "abc 012 def";

  const std::regex re1(R"((\w+) (\d+))");
  std::cmatch m1;
  std::regex_search(s, m1, re1);
  for (auto&& sub : m1) {
    std::cout << sub << std::endl;
  }
  std::cout << std::endl;

  const std::regex re2(R"((\d+) (\w+))");
  std::cmatch m2;
  std::regex_search(s, m2, re2);
  for (auto&& sub : m2) {
    std::cout << sub << std::endl;
  }
  std::cout << std::endl;

  m1.swap(m2);

  for (auto&& sub : m1) {
    std::cout << sub << std::endl;
  }
  std::cout << std::endl;
  for (auto&& sub : m2) {
    std::cout << sub << std::endl;
  }
}
```
* swap[color ff0000]
* std::regex[link ../basic_regex.md]
* std::regex_search[link ../regex_search.md]
* std::cmatch[link ../match_results.md]

### 出力
```
abc 012
abc
012

012 def
012
def

012 def
012
def

abc 012
abc
012
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
