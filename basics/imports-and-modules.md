# Import ve Modül Sistemi

{{#img-right}}turtle.svg{{/img-right}}

D dili tasarlanırken ana amaçlardan birisi de tutarlı olmak ve uç durumlardan uzak durmaktı. Bu durum [_sonuna kadar kaplumbağalar_](https://en.wikipedia.org/wiki/Turtles_all_the_way_down) olarak bilinir. Bunun güzel bir örneği ise `import` ifadesidir.

## Modül Eklemek

D dilindeki basit merhaba dünya uygulaması için, `import` gerekir. `import` ifadesi verilen `modül`deki herkese açık (public) tüm fonksiyon ve tipleri kullanılabilir/erişilebilir kılar.

### Kaplumbağalar Düşerse

Bir `import` ifadesi kaynak kodun en üst satırında bulunmak zorunda __değildir__. Fonksiyonların ya da kapsamların (scope) içerisinde de kullanılabilir. Sonraki bölümlerde bunun D dilindeki neredeyse bütün kavramlarda uygulandığını göreceksiniz. D dili nedensizce kısıtlamalar uygulamaz.

### Modülden Seçerek Eklemek

Standart kütüphane [Phobos](https://dlang.org/phobos/), `std` paketinin içindedir ve modüllere `import std.MODÜL` şeklinde erişilir.

Ayrıca `import` ifadesi modülün içinden belirli sembolleri seçmek için de kullanılabilir.

    import std.stdio : writeln, writefln;

Modülden seçerek eklemek, bir sembolün nereden geldiğini net bir şekilde belli ederek okunabilirliği arttırmak ve ayrıca farklı modüllerdeki aynı isme sahip semboller arasındaki çakışmayı engellemek için de kullanılabilir.

### Dizin ve Dosyalarla Eşleşme

D'nin modül sistemi — diğer sistemlerin aksina — tamamen dosya üzerine kuruludur. Örneğin, 'benim.kedim' her zaman `benim` klasörü içerisindeki `kedim.d` dosyasını gösterir. `benim` klasörü o anki çalışma dizini içerisinde veya tanımlanmış dizinlerden (dmd derleyicisine `-I` argümanı ile tanımlanır) birinde bulunmalıdır. Son olarak, büyük modülleri bir çok ufak dosyaya bölmek için `kedim.d` dosyası yerine `kedim/` klasörü kullanılabilir. D derleyicisi bu durumda `benim/kedim.d` dosyası yerine `benim/kedim/package.d` dosyasını yüklemeyi dener.

Genellikle (zorunlu değil) `package.d` içinde aynı dizindeki diğer modüller `public` olarak import edilir.

## {SourceCode}

```d
void main()
{
    import std.stdio;
    // veya import std.stdio : writeln;
    writeln("Merhaba Dünya!");
}
```
