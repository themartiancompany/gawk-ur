# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=4.0.1
pkgrel=1
pkgdesc="GNU version of awk"
arch=('i686' 'x86_64')
url="http://www.gnu.org/directory/GNU/gawk.html"
license=('GPL')
groups=('base')
depends=('sh' 'glibc')
provides=('awk')
install=gawk.install
source=(ftp://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig})
md5sums=('bab2bda483e9f32be65b43b8dab39fa5'
         '7cf4e4896509c655dd00ecd4ca9098ef')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}

  ./configure --prefix=/usr --libexecdir=/usr/lib
  make 
}

check() {
  cd ${srcdir}/${pkgname}-${pkgver}

  make check
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}

  make DESTDIR=${pkgdir} install

  install -dm755 ${pkgdir}/bin 
  ln -sf /usr/bin/gawk ${pkgdir}/bin/
  ln -sf gawk ${pkgdir}/bin/awk
}
