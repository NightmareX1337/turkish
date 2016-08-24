# D Diline Hoşgeldiniz

*D Programlama Dili'*nin interaktif turuna hoş geldiniz.

{{#dmanmobile}}

Bu tur size __verimli__, direk doğal makine diline derlenen bu __güçlü__ ve __ifade gücü yüksek__ dil hakkında genel bir bakış sunacaktır.

{{/dmanmobile}}

### Neden D?

D dili çeşitli diller için *derleyici geliştirmekle geçen onlarca yıllık tecrübe* sonucu oluşmuştur ve kendine özgü birçok [özelliğe](http://dlang.org/overview.html) sahiptir:

{{#dmandesktop}}

- Mükemmel modelleme gücü için _yüksek seviyeli_ dil yapısı
- Yüksek performanslı, işlemci koduna derlenen bir dil
- Statik tipleme
- C++'ın evrim geçirmiş hali (hatalı yanları olmadan)
- İşletim sistemi API'ı ve donanıma direk (katmansız) erişim
- Olağanüstü derleme hızı
- Bellek hatası olmadan programlamaya olanak tanır ([SafeD](http://dlang.org/safed.html))
- Anlaşılır, okunaklı ve bakımı kolay kod
- Diğer C ve Java gibi dillere benzerliğiyle öğrenmesi kolay
- C dili kütüphaneleriyle uyumlu (ABI compatible)
- Çok yönlü \[imperative, structured (yapısal), object oriented (nesne yönelimli), generic (değişken), functional (fonksiyonel), hatta assembly (sembolik makine kodu)\]
- Hata önleme yöntemlerine (contract programming, unit testing) tam dil desteği

... ve daha birçok [özellik](http://dlang.org/overview.html).

{{/dmandesktop}}

### Tur Hakkında

Her bölüm üzerinde oynayıp D dilinin özelliklerini deneyebileceğin kod örneklerine sahip.
'Çalıştır' butonu veya `Ctrl+Enter` tuş kombinasyonuyla kodları derlyip çalıştırabilirsiniz.


### Katıda Bulunmak

Bu tur [açık kaynaklı](https://github.com/stonemaster/dlang-tour) bir projedir ve bize bu
projenin daha da iyi olması için yapacağınız her katkı bizi çok memnun eder.

## {KaynakKod}

```d
import std.stdio;

// Haydi başlayalım!
void main()
{
    writeln("Merhaba Dunya!");
}
```
