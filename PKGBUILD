# updated by devnull [at] libcrack [dot] so
# updated by public.douglas.raillard at gmail dot com
pkgname=('radare2-bindings-git' 'radare2-pipe-git')
basename='radare2-bindings-git'
pkgver=20170809.778.b8945c9
pkgrel=2
pkgdesc="Language bindings for radare2 (git version)"
arch=('i686' 'x86_64')
url="https://radare.org"
license=('LGPL')
depends=('radare2' 'python3' 'python2')
makedepends=('git' 'swig')

source=(
  "radare2-bindings-git::git://github.com/radare/radare2-bindings.git"
  "radare2-pipe-git::git://github.com/radare/radare2-r2pipe.git"
)
md5sums=('SKIP' 'SKIP')

pkgver() {
  cd "${srcdir}/radare2-bindings-git"
  _date=`date +"%Y%m%d"`
  echo "$_date.$(git rev-list --count master).$(git rev-parse --short master)"
}


build() {
  cd "${srcdir}/radare2-bindings-git"
  ./configure \
      --prefix="/usr" \
      --enable="python"

  export PYTHON_CONFIG=python3.2-config
  make
}

package_radare2-pipe-git() {
  provides=('radare2-pipe')
  conflicts=('radare2-pipe')

  cd "${srcdir}/radare2-pipe-git/python"
  python2 setup.py install --root "${pkgdir}"
}

package_radare2-bindings-git() {
  provides=('radare2-bindings')
  conflicts=('radare2-bindings')

  cd "${srcdir}/radare2-bindings-git"
  export PYTHON_CONFIG=python3.2-config
  make DESTDIR="${pkgdir}" install
}
# vim:set ts=2 sw=2 et:
