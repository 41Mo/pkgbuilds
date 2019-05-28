# Maintainer: acxz <akashpatel2008 at yahoo dot com>
pkgname=libiges-git
pkgver=r225.efb93fd
pkgrel=1
pkgdesc="Implementation of the IGESv5.3 specification"
arch=('i686' 'x86_64')
url="http://cbernardo.github.io/libIGES"
license=('LGPL-2.1')
depends=('gcc')
makedepends=('git' 'cmake')
_name=libIGES
provides=('libiges')
conflicts=('libiges')
source=("git+https://github.com/cbernardo/libIGES.git")
md5sums=('SKIP')

pkgver() {
  cd "$_name"

  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

_buildtype="Release"

build() {

    cd "${srcdir}/${_name}"

    msg "Starting CMake (build type: ${_buildtype})"

    # Create a build directory
    mkdir -p "${srcdir}/${_name}-build"
    cd "${srcdir}/${_name}-build"

    cmake \
        -DCMAKE_BUILD_TYPE="${buildtype}" \
        -DCMAKE_INSTALL_PREFIX="/usr" \
        "${srcdir}/${_name}"

    msg "Building the project"
    make -j4
}

package() {
    cd "${srcdir}/${_name}-build"

    msg "Installing files"
    make DESTDIR="${pkgdir}/" install
}
