# Previous Maintainer: Benjamin Chretien <chretien at lirmm dot fr>
# Previous Maintainer: Gonçalo Camelo Neves Pereira <goncalo_pereira@outlook.pt>
# Previous Maintainer: midgard <arch dot midgard "at symbol" janmaes "youknowwhat" com>
# Maintainer: acxz <akashpatel2008 at yahoo dot com>
pkgname=libdart
pkgver=6.8.4
pkgrel=2
pkgdesc="Dynamic Animation and Robotics Toolkit"
arch=('i686' 'x86_64')
url="https://dartsim.github.io"
license=('BSD')
depends=('assimp' 'boost' 'eigen' 'fcl' 'libccd' 'freeglut')
optdepends=('bullet: Bullet collision detection support'
            'coin-or-ipopt: Ipopt optimizer support'
            'doxygen: required for building documentation'
            'flann: planning module support'
            'nlopt: NLopt optimizer support'
            'octomap: voxel grid shape support'
            'ode: ODE collision detection support'
            'openscenegraph: required for dart-gui-osg'
            'pagmo: pagmo optimizer support'
            'tinyxml2: parser support'
            'urdfdom: urdf parser support')
makedepends=('cmake')
_name=dart
source=(https://github.com/dartsim/${_name}/archive/v${pkgver}.tar.gz)
sha256sums=('ff6272bdfea26df1dee2a5652e7e4a4db64aa3809ddd0704c17fde8fb0b1eae3')

_buildtype="Release"

build() {
	cd "${srcdir}/${_name}-${pkgver}"

	msg "Starting CMake (build type: ${_buildtype})"

	# Create a build directory
	mkdir -p "${srcdir}/${_name}-${pkgver}/build"
	cd "${srcdir}/${_name}-${pkgver}/build"

	cmake \
		-DCMAKE_BUILD_TYPE="${_buildtype}" \
		-DCMAKE_INSTALL_PREFIX="/usr" \
    -DCMAKE_INSTALL_LIBDIR="lib" \
    "${srcdir}/${_name}-${pkgver}"

	msg "Building the project"
	make -j4
}

#check() {
#	cd "${srcdir}/${_name}-${pkgver}/build"
#	msg "Compiling unit tests"
#	make -j4 tests
#	msg "Running unit tests"
#	make test
#}

package() {
	cd "${srcdir}/${_name}-${pkgver}/build"

	msg "Installing files"
	make DESTDIR="${pkgdir}/" install

}
