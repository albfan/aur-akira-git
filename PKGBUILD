# Maintainer: Philip Goto <philip.goto@gmail.com>

pkgname=akira-git
pkgver=latest
pkgrel=1
pkgdesc="Native Linux App for UI and UX Design built in Vala and Gtk"
arch=(x86_64)
url="https://github.com/Alecaddd/Akira"
license=(GPL3)
makedepends=(granite
             gtksourceview3
             meson
             vala)
provides=(akira)
source=("git+https://github.com/Alecaddd/Akira.git")
sha256sums=(SKIP)

pkgver() {
  cd Akira
  git describe --tags --always | sed 's/-/.r/; s/-g/./'
}

prepare() {
  mkdir build
}

build() {
  cd build
  meson --prefix=/usr --buildtype=release ../Akira
  ninja
}

check() {
  cd build
  ninja test
}

package() {
  cd build
  DESTDIR="$pkgdir" ninja install
}
