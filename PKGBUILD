# Contributor: atithih <atithih -at- gmail dot com>

pkgname=hdrmerge-git
_gitname='hdrmerge'
pkgver=20150125_7f2e345
pkgrel=2
pkgdesc="HDR exposure merging software"
arch=(x86_64)
url="http://jcelaya.github.io/hdrmerge/"
license=('GPL')
depends=('libraw' 'exiv2' 'qt4' 'alglib')
makedepends=('git' 'cmake')
install=$pkgname.install
conflicts=('hdrmerge')
provides=('hdrmerge')
source=('git://github.com/jcelaya/hdrmerge.git')
md5sums=('SKIP')

pkgver() {
	cd $_gitname
	git log -1 --format='%cd_%h' --date=short | tr -d -
}


build() {
	mkdir -m755 $_gitname/build
	cd $_gitname/build
	cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release .. || return 1
}

package() {
	cd $_gitname/build

	make DESTDIR=$pkgdir/ install
	install -D -m755 hdrmerge.desktop $pkgdir/usr/share/applications/hdrmerge.desktop
	install -D -m755 ../images/icon.png $pkgdir/usr/share/icons/hdrmerge-icon.png
}
