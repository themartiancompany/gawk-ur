# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=gawk
pkgver=5.3.0
pkgrel=1
pkgdesc="GNU version of awk"
arch=(
  'arm'
  'aarch64'
  'pentium4'
  'i686'
  'x86_64'
)
url="https://www.gnu.org/software/gawk/"
license=(
  'GPL'
)
depends=(
  'glibc'
)
_os="$( \
  uname \
    -o)"
[[ "${_os}" == "GNU/Linux" ]] && \
  depends+=(
    'mpfr'
    'sh'
  )
[[ "${_os}" == "GNU/Linux" ]] && \
  depends+=(
    'libmpfr'
    'bash'
  )
provides=(
  'awk'
)
source=(
  https://ftp.gnu.org/pub/gnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig}
)
validpgpkeys=(
   # Arnold Robbins
  'D1967C63788713177D861ED7DF597815937EC0D2'
)
sha256sums=(
  '378f8864ec21cfceaa048f7e1869ac9b4597b449087caf1eb55e440d30273336'
  'SKIP'
)

build() {
  cd \
    ${pkgname}-${pkgver}
  ./configure \
    --prefix=/usr \
    --libexecdir=/usr/lib \
    --sysconfdir=/etc \
    --without-libsigsegv
  make
}

check() {
  cd ${pkgname}-${pkgver}
  make check
}

package() {
  cd ${pkgname}-${pkgver}
  make \
    DESTDIR="${pkgdir}" \
    PREFIX="/usr" \
    install
}

