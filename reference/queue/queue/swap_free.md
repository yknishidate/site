# swap (非メンバ関数)
* queue[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class T, class Container>
  void swap(queue<T, Container>& x, queue<T, Container>& y) noexcept(noexcept(x.swap(y)));
}
```

## 概要
2つの`queue`オブジェクトを入れ替える


## 効果
`x.`[`swap`](swap.md)`(y)`


## 戻り値
なし


## 例外
`x.swap(y)` が例外を投げない場合、この関数は決して例外を投げない。


## 例
```cpp example
#include <iostream>
#include <queue>

template <class Queue>
void pop_print(Queue& que)
{
  while (!que.empty()) {
    std::cout << que.front() << " ";
    que.pop();
  }
  std::cout << std::endl;
}

int main ()
{
  std::queue<int> x;
  x.push(1);
  x.push(2);
  x.push(3);

  std::queue<int> y;
  y.push(4);
  y.push(5);
  y.push(6);

  std::swap(x, y);

  pop_print(x);
  pop_print(y);
}
```
* std::swap[color ff0000]
* push[link push.md]
* que.empty()[link empty.md]
* que.front()[link front.md]
* que.pop()[link pop.md]

### 出力
```
4 5 6 
1 2 3 
```

## バージョン
### 言語
- C++11

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 4.7.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 


## 参照
