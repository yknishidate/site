# max_size
* regex[meta header]
* std[meta namespace]
* match_results[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
size_type max_size() const;
```

## 概要
`*this` に格納できるサブマッチの最大数を返す。


## 戻り値
`*this` に格納できるサブマッチの最大数


## 備考
- 本メンバ関数は [`ready`](ready.md)`() == false` でも呼び出すことが可能である。


## 例
```cpp example
#include <iostream>
#include <regex>

int main()
{
  std::cmatch m;
  std::cout << "max_size = " << m.max_size() << std::endl;
}
```
* max_size()[color ff0000]
* std::cmatch[link ../match_results.md]

### 出力例
```
max_size = 768614336404564650
```


## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5 [mark verified], 3.6 [mark verified]
- [GCC](/implementation.md#gcc): 4.9.0 [mark verified], 4.9.1 [mark verified], 5.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
