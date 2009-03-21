# Maintainer: dorphell <dorphell@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=3.1.6
pkgrel=3
pkgdesc="Gnu version of awk"
arch=(i686 x86_64)
url="http://www.gnu.org/directory/GNU/gawk.html"
license=('GPL')
groups=('base')
provides=('awk')
install=gawk.install
source=(ftp://ftp.gnu.org/pub/gnu/$pkgname/$pkgname-$pkgver.tar.gz)
depends=('bash' 'glibc')
md5sums=('b237751aef53c9ead9644e376bc53386')

build() {
  cd $srcdir/$pkgname-$pkgver
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$pkgdir install
  mv $pkgdir/usr/libexec $pkgdir/usr/lib
  install -dm755 $pkgdir/bin
  mv $pkgdir/usr/bin/gawk* $pkgdir/bin/
  mv $pkgdir/usr/bin/awk $pkgdir/bin/
  
  rm $pkgdir/usr/share/info/dir
  gzip -9 $pkgdir/usr/share/info/{gawk,gawkinet}.info
}
