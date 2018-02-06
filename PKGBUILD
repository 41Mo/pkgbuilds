# Maintainer: Darshit Shah <darnir@gmail.com>

pkgname=vgrep
pkgver=2.0.2
pkgrel=1
epoch=1
pkgdesc="Reimpementation of the ancient cgvg perl scripts"
arch=('x86_64' 'i686')
license=('GPLv3')
depends=( 'go' )
url="https://github.com/vrothberg/vgrep"
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/vrothberg/${pkgname}/archive/${pkgver}.tar.gz")
md5sums=('957e34ef84d604c3298c1fee2d015035')

prepare() {
  mkdir $srcdir/{bin,pkg,src}
  mv $srcdir/${pkgname}-${pkgver}/ $srcdir/src/
  cd $srcdir/src/$pkgname-$pkgver
}

build() {
  cd $srcdir/src/$pkgname-$pkgver
  export GOPATH=$srcdir
  go get ./...
  make release
}

package() {
  cd "$srcdir/src/$pkgname-$pkgver"

  install -m755 -d "${pkgdir}/usr/bin"
  install -m755 -t "${pkgdir}/usr/bin/" build/vgrep
}

# vim: ts=2:sw=2:et
