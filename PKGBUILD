# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=4.1.4
pkgrel=2
pkgdesc="GNU version of awk"
arch=('i686' 'x86_64')
url="http://www.gnu.org/software/gawk/"
license=('GPL')
groups=('base' 'base-devel')
depends=('sh' 'glibc' 'mpfr')
provides=('awk')
source=(ftp://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig})
md5sums=('f20c94ca51b6ebfc9bffb90f95c8ffbb'
         'SKIP')
validpgpkeys=('D1967C63788713177D861ED7DF597815937EC0D2') # Arnold Robbins

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  ./configure --prefix=/usr --libexecdir=/usr/lib --without-libsigsegv
  make
}

check() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make check
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make DESTDIR=${pkgdir} install

  #install -dm755 ${pkgdir}/bin
  #ln -sf /usr/bin/gawk ${pkgdir}/bin/
  #ln -sf gawk ${pkgdir}/bin/awk
}
