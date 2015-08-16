# Maintainer: Alexey D. <lq07829icatm at rambler.ru>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Pierre Schmitz <pierre@archlinux.de>

pkgname=kf5-akonadi-git
pkgver=r2730.fcc0439
pkgrel=1
arch=('i686' 'x86_64')
url='http://community.kde.org/KDE_PIM/Akonadi'
pkgdesc="PIM layer, which provides an asynchronous API to access all kind of PIM data"
license=('LGPL')
depends=('qt5-base' 'shared-mime-info' 'boost-libs' 'mariadb')
makedepends=('cmake' 'boost' 'postgresql' 'sqlite' 'git' 'libxslt' 'extra-cmake-modules-git')
optdepends=('postgresql: PostgreSQL backend'
            'sqlite: SQLite backend')
install=akonadi.install
conflicts=('kf5-akonadi')
provides=('kf5-akonadi')
source=("git://anongit.kde.org/akonadi.git")
md5sums=('SKIP')

pkgver() {
  cd akonadi
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir build
}

build() {
  cd build
  cmake ../akonadi \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
