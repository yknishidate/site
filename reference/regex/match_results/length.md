# length
* regex[meta header]
* std[meta namespace]
* match_results[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
difference_type length(size_type sub = 0) const;
```

## 概要
指定されたサブマッチが指す文字列の長さを返す。


## 要件
[`ready`](ready.md)`() == true`


## 戻り値
`(*this)[sub].`[`length`](../sub_match/length.md)`()`


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  const char s[] = " abc 0123 defgh ";
  const std::regex re("(\\w+) (\\d+) (\\w+)");

  std::cmatch m;
  if (std::regex_search(s, m, re)) {
    std::cout << "str() = '" << m.str() << "', length() = " << m.length() << std::endl;
    for (std::size_t i = 0, n = m.size(); i < n; ++i) {
      std::cout << "str(" << i << ") = '" << m.str(i) << "', length(" << i << ") = " << m.length(i) << std::endl;
    }
  } else {
    std::cout << "not match" << std::endl;
  }
}
```
* length[color ff0000]
* std::regex[link ../basic_regex.md]
* std::cmatch[link ../match_results.md]
* std::regex_search[link ../regex_search.md]
* m.size()[link size.md]
* m.str[link str.md]

### 出力
```
str() = 'abc 0123 defgh', length() = 14
str(0) = 'abc 0123 defgh', length(0) = 14
str(1) = 'abc', length(1) = 3
str(2) = '0123', length(2) = 4
str(3) = 'defgh', length(3) = 5
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
