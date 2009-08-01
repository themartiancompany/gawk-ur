# Maintainer: dorphell <dorphell@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=3.1.7
pkgrel=1
pkgdesc="Gnu version of awk"
arch=(i686 x86_64)
url="http://www.gnu.org/directory/GNU/gawk.html"
license=('GPL')
groups=('base')
provides=('awk')
install=gawk.install
source=(ftp://ftp.gnu.org/pub/gnu/$pkgname/$pkgname-$pkgver.tar.gz)
depends=('sh' 'glibc')
md5sums=('a38d5dec19320ace01f1d16c8beb1363')

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

