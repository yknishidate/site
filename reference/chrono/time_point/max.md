# max
* chrono[meta header]
* std::chrono[meta namespace]
* time_point[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
static constexpr time_point max();          // C++11
static constexpr time_point max() noexcept; // C++20
```

## 概要
最大の`time_point`を取得


## 戻り値
```cpp
time_point(duration::max())
```
* max()[link /reference/chrono/duration/max.md]


## 例
```cpp example
#include <iostream>
#include <chrono>

using namespace std::chrono;

int main()
{
  time_point<system_clock> p = time_point<system_clock>::max();

  std::cout << p.time_since_epoch().count() << std::endl;
}
```
* max()[color ff0000]
* system_clock[link /reference/chrono/system_clock.md]
* time_since_epoch()[link time_since_epoch.md]
* count()[link /reference/chrono/duration/count.md]

### 出力例
```
9223372036854775807
```

## バージョン
### 言語
- C++11

### 処理系
- [GCC](/implementation.md#gcc): 4.5.0 [mark verified]
- [Visual C++](/implementation.md#visual_cpp): 2012 [mark verified], 2013 [mark verified], 2015 [mark verified]


## 参照
- [P0972R0 `<chrono>` `zero()`, `min()`, and `max()` should be `noexcept`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0972r0.pdf)
