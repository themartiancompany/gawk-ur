# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=5.2.0
pkgrel=3
pkgdesc="GNU version of awk"
arch=('x86_64')
url="https://www.gnu.org/software/gawk/"
license=('GPL')
groups=('base-devel')
depends=('sh' 'glibc' 'mpfr')
provides=('awk')
options=('debug')
source=(https://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig}
        0001-Add-missing-UPREF.patch)
validpgpkeys=('D1967C63788713177D861ED7DF597815937EC0D2') # Arnold Robbins
sha256sums=('ef5af4449cb0269faf3af24bf4c02273d455f0741bf3c50f86ddc09332d6cf56'
            'SKIP'
            'd39fa487f89c743ba55ed0b5eeb9fe33db4bd7010bf5f61f8aa1a9541a18775e')

prepare() {
  cd ${pkgname}-${pkgver}

  # https://bugs.gentoo.org/868567
  patch -Np1 -i ../0001-Add-missing-UPREF.patch
}

build() {
  cd ${pkgname}-${pkgver}
  ./configure --prefix=/usr --libexecdir=/usr/lib --sysconfdir=/etc --without-libsigsegv
  make
}

check() {
  cd ${pkgname}-${pkgver}
  make check
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
}
