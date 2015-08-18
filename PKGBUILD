# Maintainer:  Federico Cinelli <cinelli.federico@gmail.com>
# Contributor: Egor Pomortsev <egor.pomortsev@gmail.com>
# Contributor: M Rawash <mrawash@gmail.com>
# Contributor: Andrzej Giniewicz <gginiu@gmail.com>

pkgname=xf86-input-wacom-git
pkgver=0.20.0+7
pkgrel=2
pkgdesc="X.Org Wacom tablet driver (from git)"
url="http://linuxwacom.sourceforge.net"
arch=(i686 x86_64)
license=(GPL)
depends=(libxi libxinerama libxrandr)
makedepends=(autoconf automake git xorg-server-devel libxext xorg-util-macros)
provides=("xf86-input-wacom=$pkgver")
conflicts=(xf86-input-wacom)
options=(!libtool)
backup=(etc/X11/xorg.conf.d/50-wacom.conf)

source=("git://git.code.sf.net/p/linuxwacom/xf86-input-wacom")
md5sums=('SKIP')

pkgver() {
  cd xf86-input-wacom
  git describe | sed -r 's/^xf86-input-wacom-([^-]+)-([0-9]+)-g.*$/\1+\2/'
}

prepare() {
  mkdir xf86-input-wacom/m4
}

build() {
  cd xf86-input-wacom
  ./autogen.sh --prefix=/usr --with-xorg-conf-dir=/etc/X11/xorg.conf.d
  make
}

check() {
  cd xf86-input-wacom
  make -k check || :
}

package() {
  cd xf86-input-wacom
  make DESTDIR="$pkgdir" install
}

