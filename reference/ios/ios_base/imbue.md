# imbue
* ios[meta header]
* function[meta id-type]
* std[meta namespace]
* ios_base[meta class]

```cpp
locale imbue(const locale& loc);
```
* locale[link ../../locale/locale.md]

## 概要
ロケールを設定する。


## 効果
`*this` で使用するロケールを引数 `loc` に設定した後、[`register_callback`](register_callback.md) で登録されたペア `(fn, index)` を `(*fn)(`[`imbue_event`](type-event.md)`, *this, index)` として呼び出す。


## 戻り値
[`getloc`](getloc.md)`()` の変更前の値


## 備考
- 呼び出されたコールバック関数の内部で [`getloc`](getloc.md)`()` を呼び出した場合、新たに設定されたロケール（つまり引数 `loc` で指定されたロケール）が返される。
- 設定されたロケールは、ロケール依存の入出力に使用される。ただし、[`ios_base`](../ios_base.md) 自体にはロケール依存の入出力関数は存在しない。実際にロケール依存の入出力を行うのは、派生クラスである [`basic_istream`](../../istream/basic_istream.md) と [`basic_ostream`](../../ostream/basic_ostream.md)（および、それらの派生クラス [`basic_iostream`](../../istream/basic_iostream.md)）である。


## 例
```cpp example
#include <iostream>
#include <locale>

int main()
{
  std::cout.imbue(std::locale::classic());
  std::cout << 1234.5 << std::endl;
  std::cout.imbue(std::locale("en_US"));
  std::cout << 1234.5 << std::endl;
  std::cout.imbue(std::locale("de_DE"));
  std::cout << 1234.5 << std::endl;
}
```
* imbue[color ff0000]
* std::locale[link ../../locale/locale.md]
* classic[link ../../locale/classic.md.nolink]

### 出力例
```
1234.5
1,234.5
1.234,5
```

なお、ロケールの名称（ここでは `en_US` と `de_DE`）は環境依存のため、上記の例は動作しないこともある。  
その場合でも、ロケールの名称を当該環境で適切なものに変更すれば動作するはずである。  
また、最初の行（`C` ロケール）以外の出力はロケール依存のため、たとえこれらのロケールが使用できたとしても上記のようには出力されない可能性もある（が、一般的にはこのように出力される）。


## バージョン
## 言語
- C++98

### 処理系
- [Clang](/implementation.md#clang): 3.0 [mark verified], 3.1 [mark verified], 3.2 [mark verified], 3.3 [mark verified], 3.4 [mark verified], 3.5.0 [mark verified], 3.6.0 [mark verified], 3.7.0 [mark verified], 3.8.0 [mark verified]
- [GCC](/implementation.md#gcc): 4.3.6 [mark verified], 4.4.7 [mark verified], 4.5.4 [mark verified], 4.6.4 [mark verified], 4.7.3 [mark verified], 4.8.1 [mark verified], 4.8.2 [mark verified], 4.9.0 [mark verified], 4.9.1 [mark verified], 4.9.2 [mark verified], 5.1.0 [mark verified], 5.2.0 [mark verified], 6.0.0 [mark verified]
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


## 参照
- [`ios_base`](../ios_base.md)`::`[`event`](type-event.md)
- [`ios_base`](../ios_base.md)`::`[`event_callback`](type-event_callback.md)
- [`ios_base`](../ios_base.md)`::`[`register_callback`](register_callback.md)
- [`ios_base`](../ios_base.md)`::`[`getloc`](getloc.md)
- [`basic_ios`](../basic_ios.md)`::`[`imbue`](../basic_ios/imbue.md)
- [`basic_streambuf`](../../streambuf/basic_streambuf.md)`::`[`getloc`](../../streambuf/basic_streambuf/getloc.md)
- [`basic_streambuf`](../../streambuf/basic_streambuf.md)`::`[`pubimbue`](../../streambuf/basic_streambuf/pubimbue.md)
- [`locale`](../../locale/locale.md)
