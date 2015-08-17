# Maintainer:
# Contributor: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>

pkgname=orpheus
pkgver=1.6
pkgrel=5
pkgdesc="Light-weight text mode menu- and window-driven audio player application for various formats"
arch=('i686' 'x86_64')
url="http://thekonst.net/orpheus/"
license=('GPL')
depends=('ncurses' 'vorbis-tools' 'mpg123' 'libcddb' 'libxml2')
source=(http://thekonst.net/download/$pkgname-$pkgver.tar.bz2
        orpheus-1.6-nolibghttp.patch)
sha256sums=('541a22733c190bd7fa2ef514a8905f15b7cb8e1032b7678792d2da1f09f2a01c'
            '50498893d1463b6b1a7fc83b508b66a9e9c8eb530430eb1f0fffecc97ccb0147')

build() {
  cd "${srcdir}"/$pkgname-$pkgver

  patch -Np0 -i "${srcdir}"/orpheus-1.6-nolibghttp.patch

  cd kkstrtext-0.1
  ./configure --prefix=/usr
  cd ../kkconsui-0.1
  ./configure --prefix=/usr
  cd ../
  ./configure --prefix=/usr

  make
}

package() {
  cd "${srcdir}"/$pkgname-$pkgver

  make DESTDIR="${pkgdir}" install
}
