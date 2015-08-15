# Contributor: Martin Stolpe <martinstolpe [at] gmail ... com>

pkgname=elflibviewer
pkgver=0.9
pkgrel=3
pkgdesc="Dependency tree viewer of ELF libraries"
arch=('i686' 'x86_64')
url="http://www.purinchu.net/software/elflibviewer.php"
license=('GPL')
depends=('qt4' 'hicolor-icon-theme')
makedepends=()
install='elflibviewer.install'
source=(http://www.purinchu.net/software/$pkgname-$pkgver.tar.bz2
  CMakeLists.txt.diff)

build() {
  cd "$srcdir/$pkgname-$pkgver"
  patch -p1 -i ../CMakeLists.txt.diff || return 1

  [[ -d build ]] && rm -rf build
  mkdir -p "$srcdir/$pkgname-$pkgver/build"
  cd  "$srcdir/$pkgname-$pkgver/build"
  cmake -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr ../ \
    -DQT_QMAKE_EXECUTABLE=qmake-qt4
  make || return 1
  make DESTDIR=$pkgdir install
}
md5sums=('b1b3c47b56b3b53ae5bde8744d798a23'
         '81dc904a0ba8edd1f0a895b3073008b4')
