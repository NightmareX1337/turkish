# Hafıza

D bir sistem programlama dili olduğundan manuel hafıza yönetimine (manual memory management) izin verir. Ancak bu oldukça hataya meyilli bit yöntem olması nedeniyle D dili hafıza ayırma için varsayılan olarak *çöp toplayıcı* (GC:garbage collector) kullanır.

D, C'deki gibi işaretçi (pointer) türlerine `T*` sahiptir:

    int a;
    int* b = &a; // b contains address of a
    auto c = &a; // c is int* and contains address of a

Yığın (heap) üzerinde yeni bir hafıza ayırmak için çöp toplayıcı tarafından yönetilen (managed) bir işaretçi döndüren `new` ifadesi kullanılır:

    int* a = new int;

`a`'nın gösterdiği hafıza herhangi bir işaretçi tarafından artık gösterilmediği zaman çöp toplayıcı kullanılan hafızayı iade eder.

D dili fonksiyonlar için üç adet güvenlik seviyesine sahiptir: `@system`, `@trusted`, `@safe`
Aksi belirtilmediği sürece varsayılan seviye `@system` olur. `@safe`, D'nin yalnızca hafıza hatalarına yol açmayan özelliklerini kullanmanıza olanak tanır. `@safe` kod yalnızca `@safe` yada `@trusted` fonksiyonları çağırabilir. Ek olarak, `@safe` kod içinde işaretçi aritmetiği yapmaya izin verilmez:

    void main() @safe
	{
        int a = 5;
        int* p = &a;
        int* c = p + 5; // error
    }

`@trusted` fonksiyonlar SafeD ile düşük-seviyeli güvensiz kod arasında köprü görevi gören elle doğrulanmış fonksiyonlardır.

### Detaylı

* [SafeD](https://dlang.org/safed.html)

## {SourceCode}

```d
import std.stdio : writeln;

void güvenliFonk() @safe
{
    writeln("Merhaba Dünya");
    // Çöp toplayıcı ile hafıza ayırmak da güvenlidir
    int* p = new int;
}

void güvensizFonk()
{
    int* p = new int;
    int* fiddling = p + 5;
}

void main()
{
    güvenliFonk();
    güvensizFonk();
}
```
