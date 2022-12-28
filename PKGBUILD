

pkgname=mymc
pkgver=2.6
pkgrel=11
pkgdesc="A public domain utility for working with PlayStation 2 memory card images"
arch=(any)
url="http://www.csclub.uwaterloo.ca:11068/mymc"
license=('custom:public domain')
depends=(python2-wxpython3)
makedepends=(dos2unix)
_commit="04dd9c490b0d8b59e6bae2e60284e29c1fc2e448"
source=("mymc-$pkgver.zip::https://github.com/Ben0mega/mymc/archive/$_commit.zip"
        "mymc.sh"
        "mymc-gui.sh"
        "mymc.desktop"
        "mymc.png")
sha256sums=('511639be6b9cadcea45461e33612b7a26a0af54ba123f059e338e21da078cb04'
            'd10616d21e04c0d3b63d3dd995279107b20306e2d70690c06328683714312792'
            'dea7982ca8d9c95441aec91846c4d6e14c248c939b828c35a991bebb43050838'
            '335b4754d93bee9d66c46f9516a76859e451aeeaa03e478abe5263d19221c586'
            '27e07106eb41c719a870821fd38804ba3f11740742e30bb4e032b4b346738fae')

prepare() {
    cd "$srcdir/mymc-$_commit"
    dos2unix *.py
}

build() {
    cd "$srcdir/mymc-$_commit"
    python2 -m compileall .
}

package() {
    cd "$srcdir/mymc-$_commit"
    install -d  "$pkgdir/usr/bin"
    cp "$srcdir/mymc.sh" "$pkgdir/usr/bin/mymc"
    cp "$srcdir/mymc-gui.sh" "$pkgdir/usr/bin/mymc-gui"
    chmod 755 "$pkgdir/usr/bin/mymc"{,"-gui"}
    install -Dt "$pkgdir/usr/share/mymc/"         -m755 *.py *.pyc
    install -Dt "$pkgdir/usr/share/doc/mymc/"     -m644 *.txt
    install -Dt "$pkgdir/usr/share/applications/" -m644 "$srcdir/mymc.desktop"
    install -Dt "$pkgdir/usr/share/pixmaps/"      -m644 "$srcdir/mymc.png"
}
