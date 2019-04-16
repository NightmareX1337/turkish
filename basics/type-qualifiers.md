# Değişkenlik

D statik türlü bir dildir: bir değişken tanımlandıktan sonra türü değişmez. Bu, derleyicinin hataları derleme sırasında önlemesini ve belli kısıtlamaları mecbur kılmasını sağlar. İyi bir tür-güvenliği (type-safety) büyük programları daha sürdürülebilir ve bakım yapılabilir (maintainable) kılan desteği sağlar.

D dilinde birçok tür niteleyici (type qualifier) bulunur. En çok kullanılanları `const` ve `immutable`'dır.

### `immutable`

D dili statik bi tür sistemine ek olarak belli kısıtlamaları zorunlu kılan tür niteliklerine (bazen "tür kurucu" (type constructors) da denen) sahiptir. Örneğin `immutable` bir değişken yalnızca ilk değer atamaya izin verir ve sonra değiştirilemez.

    immutable int err = 5;
    // yada: immutable err = 5 yazarsak
	// derleyici türü otomatik int alır.
    err = 5; // derlenmez!

`immutable` nesneler farklı işlem kanalları (thread) arasında senkronizasyon gerekmeden paylaşılabilir çünkü tanım gereği asla değeri değiştirilemez. Bu nesneler aynı zamanda mükemmel bir şekilde önbelleklenebilir (cache).

### `const`

`const` nesneler de değiştirilemez ancak bu kısıtlama yalnızca içinde bulunduğu kapsamda geçerlidir. `const` bir işaretçi hem *mutable* hem de `immutable` bir nesneden oluşturulabilir. Bu durumda nesne `const` işaretçi üzerinden değiştirilemezse bile normal bir referans aracılığıyla değişmesi mümkündür. API'ların argüman alırken `const` kullanarak hem `immutable` hem de normal değişkenleri kabul etmesi oldukça sık karşılaşılan bir durumdur.

    void foo(const char[] s)
    {
        // Eğer sonraki satır koda eklenirse
        // hata verir (const nesne değiştirilemez):
        // s[0] = 'x';

        import std.stdio : writeln;
        writeln(s);
    }

    // `const` sayesinde iki fonksiyon çağrısı da sorunsuz derlenir:
    foo("abcd"); // karakter dizileri immutable'dır
    foo("abcd".dup); // .dup değiştirilebilir bir kopya verir

Hem `immutable` hem de `const` _geçişli_ tür nitelikleridir, uygulandığı nesne üzerinden erişilebilen bütün alt nesnelere de uygulanır.

### Detaylı

#### Temel Kaynaklar

- [Değişmezlik](http://ddili.org/ders/d/const_ve_immutable.html)
- [Kapsamlar, İsim Alanı](http://ddili.org/ders/d/isim_alani.html)

#### İleri Seviye Kaynaklar

- [const sıkça sorulan sorular](https://dlang.org/const-faq.html)
- [D dilinde tür nitelikleri](https://dlang.org/spec/const3.html)

## {SourceCode}

```d
import std.stdio : writeln;

void main()
{
    /**
    * Değişkenler varsayılan olarak değiştirilebilir:
    */
    int m = 100;
    writeln("m: ", typeof(m).stringof);
    m = 10; // sorun yok

    /**
    * Değiştirilebilir hafızayı göstermek:
    */
    // const bir işaretçiye izin verilir
    const int* cm = &m;
    writeln("cm: ", typeof(cm).stringof);
    // Tanım gereği `const` değiştirilemez:
    // *cm = 100; // hata!

    // `immutable` nesne asla değişmeyeceği
    // garanti olduğundan değişken hafızayı
    // gösteremez
    // immutable int* im = &m; // hata!

    /**
    * Salt-okunur hafızayı göstermek:
    */
    immutable v = 100;
    writeln("v: ", typeof(v).stringof);
    // v = 5; // hata!

    // `const` salt-okunur, hafızayı gösterebilir,
    // ama kendi de salt-okunurdur
    const int* cv = &v;
    writeln("cv: ", typeof(cv).stringof);
    // *cv = 10; // hata!
}
```
