# lock
* shared_mutex[meta header]
* std[meta namespace]
* shared_mutex[meta class]
* function[meta id-type]
* cpp17[meta cpp]

```cpp
void lock();
```

## 概要
排他ロックを取得する。


## 要件
この関数を呼び出したスレッドが、ミューテックスの排他所有権と共有所有権のいずれもを保持していないこと。


## 効果
この関数を呼び出したスレッドがミューテックスの排他所有権を取得できるまでブロックする。


## 戻り値
なし


## 例外
この関数は、以下のerror conditionを持つ[`system_error`](/reference/system_error/system_error.md)例外オブジェクトを送出する可能性がある：

- [`operation_not_permitted`](/reference/system_error/errc.md) : スレッドにこの操作を行う権限がない
- [`resource_deadlock_would_occur`](/reference/system_error/errc.md) : デッドロックが発生することを検出した(実装依存)
- [`device_or_resource_busy`](/reference/system_error/errc.md) : ミューテックスがすでにロックされていて、ブロッキングできない


## 例
```cpp example
#include <thread>
#include <shared_mutex>

class X {
  mutable std::shared_mutex mtx_;
  int value_ = 0;
public:
  // メンバ変数value_への書き込みを排他的にする
  void add_value(int value)
  {
    mtx_.lock(); // 排他ロックを取得する
    value_ = value;
    mtx_.unlock(); // 排他ロックを手放す
  }

  // メンバ変数value_の値を読み込む
  int get_value() const
  {
    int result = 0;
    mtx_.lock_shared(); // 共有ロックを取得する
    result = value_;
    mtx_.unlock_shared(); // 共有ロックを手放す
    return result;
  }
};

int main()
{
  X x;

  std::thread t1([&x]{ x.add_value(1); int value = x.get_value(); });
  std::thread t2([&x]{ x.add_value(2); int value = x.get_value(); });

  t1.join();
  t2.join();
}
```
* lock()[color ff0000]
* unlock()[link unlock.md]
* lock_shared()[link lock_shared.md]
* unlock_shared()[link unlock_shared.md]

### 出力
```
```

## バージョン
### 言語
- C++17

### 処理系
- [Clang](/implementation.md#clang): 3.7.1 [mark verified]
- [GCC](/implementation.md#gcc): 6.3 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??
