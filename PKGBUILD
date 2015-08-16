# Maintainer: Daniel Beal (killerbyte at xram dot co)

pkgname='lottoshares-qt'
pkgver=1.0.6
pkgrel=1
arch=('i686' 'x86_64')
url="http://lottoshares.org/"
makedepends=('boost' 'automoc4' 'qrencode' 'miniupnpc')
license=('MIT')
pkgdesc="Peer-to-peer network based digital currency (QT)"
depends=(boost-libs qt4 miniupnpc qrencode)
conflicts=(lottoshares)
install=lottoshares-qt.install
source=("https://github.com/lottoshares/lottoshares/archive/$pkgver.tar.gz"
        "$pkgname.desktop")
sha256sums=('91129ace4e390496f4f83d46e6da9c570996f6cc4012870ea979f4a06f6f7e36'
            '3bb206eaace2f8a9c646b1ed411c3aba74ec3f393489ec56329d7837d55b0e27')

build() {
  cd "$srcdir/lottoshares-$pkgver"

  # and make qt gui
  qmake-qt4 USE_QRCODE=1 USE_UPNP=1
  make
}


package() {
  install -Dm644 lottoshares-qt.desktop "$pkgdir"/usr/share/applications/lottoshares.desktop
  cd "$srcdir/lottoshares-$pkgver"
  install -Dm755 lottoshares-qt "$pkgdir"/usr/bin/lottoshares-qt
  install -Dm644 share/pixmaps/bitcoin128.png "$pkgdir"/usr/share/pixmaps/lottoshares128.png

  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

