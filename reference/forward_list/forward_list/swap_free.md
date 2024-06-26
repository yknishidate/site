# swap (非メンバ関数)
* forward_list[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class T, class Allocator>
  void swap(forward_list<T, Allocator>& x,
            forward_list<T, Allocator>& y);  // (1) C++11

  template <class T, class Allocator>
  void swap(forward_list<T,Allocator>& x,
            forward_list<T,Allocator>& y)
              noexcept(noexcept(x.swap(y))); // (1) C++17
}
```

## 概要
2つの`forward_list`オブジェクトを入れ替える。


## 効果
`x.`[`swap`](swap.md)`(y)`


## 戻り値
なし


## 例
```cpp example
#include <iostream>
#include <forward_list>
#include <string>
#include <algorithm> // std::for_each

template <class T>
void print(const std::string& name, const std::forward_list<T>& ls)
{
  std::cout << name << " : {";
  std::for_each(ls.begin(), ls.end(), [](const T& x) { std::cout << x << " "; });
  std::cout << "}" << std::endl;
}

int main()
{
  std::forward_list<int> ls1 = {4, 5, 6};
  std::forward_list<int> ls2 = {1, 2, 3};

  std::swap(ls1, ls2);

  print("ls1", ls1);
  print("ls2", ls2);
}
```
* std::swap[color ff0000]
* ls.begin()[link begin.md]
* ls.end()[link end.md]

### 出力
```
ls1 : {1 2 3 }
ls2 : {4 5 6 }
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
- [N4258 Cleaning-up noexcept in the Library, Rev 3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)
    - `noexcept` 追加の経緯となる提案文書
