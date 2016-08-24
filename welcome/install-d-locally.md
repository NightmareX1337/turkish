# D'yi Bilgisayarınıza Kurun

D Dilinin [dlang.org](https://dlang.org) web sitesinden referans derleyici **DMD'**nin (Digital Mars D) son sürümü [indirilip](http://dlang.org/download.html) kurulabilir:

### Windows

* [Kurulum dosyası](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd-{{latest-release}}.exe)
* veya sıkıştırılmış [7zip arşivi](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.windows.7z)
* [chocolatey](https://chocolatey.org/packages/dmd) kullanarak: `choco install dmd`

### Mac OS

* `.dmg` [dosyası](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.dmg)
* veya sıkıştırılmış [Arşiv dosyası](http://downloads.dlang.org/releases/2.x/{{latest-release}}/dmd.{{latest-release}}.osx.tar.xz)
* [Homebrew](http://brew.sh) üzerinden: `brew install dmd`

### Linux / FreeBSD / Mac OS

Derleyiciyi (dmd) çabucak kullanıcı dizinine kurmak için terminalde şunu çalıştırabilirisiniz: `curl -fsS https://dlang.org/install.sh | bash -s dmd`

Çeşitli Linux sürümleri için kurulum paketlerini bulabilirsiniz:

* [ArchLinux](https://wiki.archlinux.org/index.php/D_(programming_language)
* [Debian/Ubuntu](http://d-apt.sourceforge.net)
* [Fedora/CentOS](http://dlang.org/download.html#dmd)
* [Gentoo](https://wiki.gentoo.org/wiki/Dlang)
* [OpenSuse](http://dlang.org/download.html#dmd)

### Diğer Derleyiciler

DMD derleyicisi dışında da farklı derleyici alt yapısını kullanan derleyiciler bulunmakta ve bunları [dlang.org](https://dlang.org) sitesinin indirmeler (downloads) bölümünde bulabilirsiniz:

* GCC altyapısını kullanan [**GDC**](http://gdcproject.org/downloads)
* LLVM altyapısını kullanan [**LDC**](https://github.com/ldc-developers/ldc#installation)

GDC ve LDC her zaman DMD derleyicisi gibi güncel front-end sürümüne sahip
olmayabilir ancak genellikle optimizasyon yeteneği, desteklediği
işlemci mimarisi ve platformlar (örneğin ARM) daha fazladır.

Daha fazla bilgi için [wiki](https://wiki.dlang.org/Compilers) sayfasına bakabilirsiniz.
