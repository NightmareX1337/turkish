# Temel Veri Tipleri

D dilinde platformdan **bağımsız** olarak her zaman aynı boyutta olan temel veri tipleri vardır. Tek istisna, mümkün olan en geniş aralıkta kayan noktalı sayıları (floating point) sağlayan `real` veri tipidir. Uygulamanın 32-bit veya 64-bit derlenmesi tam sayı (int, long...) tiplerinin boyutunda herhangi bir değişikliğe neden olmaz.

| tür                           | boyut
|-------------------------------|------------
|`bool`                         | 8-bit
|`byte`, `ubyte`, `char`        | 8-bit
|`short`, `ushort`, `wchar`     | 16-bit
|`int`, `uint`, `dchar`         | 32-bit
|`long`, `ulong`                | 64-bit

#### Kayan Noktalı Sayı Tipleri:

| tür     | boyut
|---------|--------------------------------------------------
|`float`  | 32-bit
|`double` | 64-bit
|`real`   | >= 64-bit (genellikle 64-bit, Intel x86 için 80-bit)

`u` öneki *işaretsiz* (unsigned) tip anlamına gelir. `char` UTF-8 karakterini ifade eder, `wchar` UTF-16 karakter dizisinde (string) ve `dchar` UTF-32 karakter dizisinde kullanılır.

Derleyici farklı tipdeki değişkenler arasında tür dönüşümlerine (cast) veri kaybı olmadığı sürece izin verir. Ancak kayan noktalı sayılar arasındaki (örneğin `double` -> `float`) dönüşümlere her zaman izin verilir.

Özellikle başka bir veri tipine dönüşüm yapmak istediğinizde `cast(TÜR) değişken` ifadesiyle yapabilirsiniz. Fakat bu özellik dikkatlice kullanılmalıdır. `cast` ifadesi tür yapısını bozabilir.

`auto` anahtar kelimesiyle değişken oluşturduğunuzda derleyici değişkene atadığınız ilk değere (initialization) bakarak değişkenin tipini otomatik belirler. `auto derece = -273.15f` ifadesinde `derece` değişkenin tipi `float` olur. Değişkenin türünün çalışma zamanında değişmediğine dikkat edin, otomatik tür belirleme derleme sırasında gerçekleşir ve aynı kalır.

### Tür Nitelikleri

Tüm veri türlerinin varsayılan değerini gösteren `.init` niteliği vardır. Bütün tam sayılar için `0` ve kayan noktalı sayılar için ise `nan` (*not a number* / *sayı değil*) varsayılan değerdir.

Tam sayı ve kayan noktalı sayılarda, tutabilecekleri en yüksek değeri gösteren `.max` niteliği vardır. Tam sayılara aynı zamanda tutabildiği en küçük değeri ifade eden `.min` niteliğine sahipken kayan noktalı sayılarda 0'dan farklı en küçük normalize değeri ifade eden `.min_normal` niteliğine sahiptir.

Kayan noktalı sayılar ayrıca `.nan` (NaN değeri), `.infinity` (sonsuz değeri), `.dig` (ondalık basamak sayısı/hassasiyeti), `.mant_dig` (mantissadaki bit sayısı) gibi daha bir çok niteliğe sahiptir.

Her türün ayrıca ismini karakter dizisi olarak döndüren `.stringof` niteliği vardır.

### D Dilinde İndeksler

D dilinde indeksler genellikle `size_t` türünü kullanır. Bu tür erişilebilir bütün hafızayı temsil etmek için yeterli büyüklükte tanımlanmıştır. 32-bit mimari için `uint`, 64-bit mimari içinse `ulong` veri türünü ifade eder.

### Assert İfadeleri

`assert(koşul)` sadece debug modunda çalışıp koşulları doğrulayan ve koşul sağlanamadığında `AssertionError` ile programı durduran bir ifadedir.
Bu yüzden `assert(0)` erişilemez kodu işaretlemek için kullanılır.

### Detaylı

#### Temel Kaynaklar

- [Atama](http://ddili.org/ders/d/atama_ve_sira.html)
- [Değişkenler](http://ddili.org/ders/d/degiskenler.html)
- [Aritmetik](http://ddili.org/ders/d/aritmetik_islemler.html)
- [Kesirli Sayılar](http://ddili.org/ders/d/kesirli_sayilar.html)
- [_D Programlama Dilinde_ Temel Türler](http://ddili.org/ders/d/temel_turler.html)

#### İleri Seviye Kaynaklar

- [D dilindeki bütün veri türlerine genel bakış](https://dlang.org/spec/type.html)
- [`auto` ve `typeof`](http://ddili.org/ders/d/auto.html)
- [Tür Nitelikleri](http://www.ddili.org/ders/d/nitelikler.html)
- [Assert İfadesi](http://www.ddili.org/ders/d/assert.html)

## {SourceCode}

```d
import std.stdio : writeln;

void main()
{
    // Büyük sayılar okunabilirliği
    // artırmak için "_"
    // ile ayrılabilir.
    int b = 7_000_000;
    short c = cast(short) b; // dönüşüm gerekli
    uint d = b; // sorun yok
    int g;
    assert(g == 0);

    // f eki float olduğunu belirtir
    auto f = 3.1415f;

    // typeid(DEĞİŞKEN) ifadenin
    // tür bilgisini döndürür
    writeln("f nin türü = ", typeid(f));
    double pi = f; // sorun yok
    // kayan noktalı sayı türleri için
    // daha küçük kayan noktalı sayılara
    // dönüşüme izin verilir
    float daha_küçük = pi;

    // Tür niteliklerine erişim
    assert(int.init == 0);
    assert(int.sizeof == 4);
    assert(bool.max == 1);
    writeln(int.min, " ", int.max);
    writeln(int.stringof); // int
}
```
