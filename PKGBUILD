# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=4.1.0
pkgrel=1
pkgdesc="GNU version of awk"
arch=('i686' 'x86_64')
url="http://www.gnu.org/software/gawk/"
license=('GPL')
groups=('base' 'base-devel')
depends=('sh' 'glibc' 'mpfr')
provides=('awk')
install=gawk.install
source=(ftp://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig})
md5sums=('13e02513105417818a31ef375f9f9f42'
         'SKIP')

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
