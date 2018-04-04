# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Your Name <youremail@domain.com>
pkgname="cantata-master"
pkgver=d5cc85
pkgrel=1
epoch=
pkgdesc=""
arch=('any')
url=""
license=('GPL')
groups=()
depends=()
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("git+https://github.com/CDrummond/cantata.git")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
    cd cantata 
    git rev-parse HEAD | sed -E 's/^(......).*/\1/g'
}


prepare(){
	mkdir build
	cd build
	cmake -DSHARE_INSTALL_PREFIX=/usr/share \
	      -DCMAKE_INSTALL_PREFIX=/usr \
	      -DCMAKE_CXX_COMPILER=/lib/ccache/bin/g++ \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DENABLE_LIBVLC=0 \
	      ../cantata 
}


build() {
	cd build
	make -j4
}


package() {
	cd build
	make DESTDIR="$pkgdir" install
}
