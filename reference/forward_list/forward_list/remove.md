# remove
* forward_list[meta header]
* std[meta namespace]
* forward_list[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
void remove(const T& value);      // (1) C++11
size_type remove(const T& value); // (1) C++20
```

## 概要
指定された値の要素を全て削除する。


## 効果
コンテナの全ての要素に対する各イテレータ`i`において、`*i == value`による比較が`true`となる要素を削除する。

削除された要素に対するイテレータおよび参照は無効となる。


## 戻り値
- C++11 : なし
- C++20 : 削除された要素数を返す


## 例外
型`T`の等値比較が例外を投げなければ、この関数は例外を投げない


## 計算量
ちょうど`distance(begin(), end())`回だけ等値比較を行う


## 例
```cpp example
#include <iostream>
#include <forward_list>

int main()
{
  std::forward_list<int> ls = {3, 1, 4, 1};

  ls.remove(1); // 値1の要素を全て削除

  for (int x : ls) {
    std::cout << x << std::endl;
  }
}
```
* remove[color ff0000]

### 出力
```
3
4
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 4.7.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 2010 [mark verified], 2012 [mark verified], 2013 [mark verified], 2015 [mark verified], 2017 [mark verified]


## 参照
- [P0646R1 Improving the Return Value of Erase-Like Algorithms I: list/forward list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0646r1.pdf)
