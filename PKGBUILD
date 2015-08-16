# $Id$
# Nicolas Boichat <nicolas@boichat.ch>
# Adapted from sbc by Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

_pkgbasename=sbc
pkgname=lib32-$_pkgbasename
pkgver=1.3
pkgrel=1
pkgdesc="Bluetooth Subband Codec (SBC) library (32-bit)"
arch=('x86_64')
url="http://www.bluez.org/"
license=('GPL' 'LGPL')
depends=('glibc' $_pkgbasename)
makedepends=(gcc-multilib)
source=(http://www.kernel.org/pub/linux/bluetooth/$_pkgbasename-$pkgver.tar.xz)
md5sums=('2d8b7841f2c11ab287718d562f2b981c')

build() {
  cd $_pkgbasename-$pkgver

  export CC="gcc -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  ./configure --prefix=/usr --disable-static --disable-tester \
              --libdir=/usr/lib32
  make
}

package() {
  cd $_pkgbasename-$pkgver
  make DESTDIR="$pkgdir" install
  rm -rf "${pkgdir}"/usr/{include,share,bin}
  mkdir -p "$pkgdir/usr/share/licenses"
  ln -s $_pkgbasename "$pkgdir/usr/share/licenses/$pkgname"
}
