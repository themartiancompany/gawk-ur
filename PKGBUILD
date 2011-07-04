# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=4.0.0
pkgrel=1
pkgdesc="GNU version of awk"
arch=('i686' 'x86_64')
url="http://www.gnu.org/directory/GNU/gawk.html"
license=('GPL')
groups=('base')
depends=('sh' 'glibc')
provides=('awk')
install=gawk.install
source=(ftp://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz)
md5sums=('51e417b71287629940051e6f652c6492')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}

  ./configure --prefix=/usr --libexecdir=/usr/lib
  make 
}

check() {
  cd ${srcdir}/${pkgname}-${pkgver}

  make -j1 check
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}

  make DESTDIR=${pkgdir} install

  install -dm755 ${pkgdir}/bin 
  mv ${pkgdir}/usr/bin/gawk* ${pkgdir}/bin/
  ln -sf gawk ${pkgdir}/bin/awk
  ln -sf /bin/gawk ${pkgdir}/usr/bin/
}
