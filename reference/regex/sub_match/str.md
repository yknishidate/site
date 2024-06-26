# str
* regex[meta header]
* std[meta namespace]
* sub_match[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
string_type str() const;
```

## 概要
マッチした文字列を `string_type` 型で返す。キャストと同じ。


## 戻り値
`matched ? string_type(first, second) : string_type()`


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  const char s[] = "123";
  const std::regex re(R"(\d+)");
  std::cmatch m;
  if (std::regex_search(s, m, re)) {
    std::csub_match sub = m[0];
    if (sub.matched) {
      std::cout << '\'' << sub.str() << '\'' << std::endl;
      sub.matched = false;
      std::cout << '\'' << sub.str() << '\'' << std::endl;
    } else {
      std::cout << "not participate" << std::endl;
    }
  } else {
    std::cout << "not match" << std::endl;
  }
}
```
* str()[color ff0000]
* std::regex[link ../basic_regex.md]
* std::cmatch[link ../match_results.md]
* std::regex_search[link ../regex_search.md]
* std::csub_match[link ../sub_match.md]

### 出力
```
'123'
''
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
