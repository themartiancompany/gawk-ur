# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
  _mpfr='mpfr'
  _shell="sh"
elif [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
  _mpfr='libmpfr'
  _shell='bash'
fi
_pkg=gawk
pkgname="${_pkg}"
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
  "${_libc}"
  "${_mpfr}"
  "${_shell}"
)
provides=(
  'awk'
)
_http="https://ftp.gnu.org/pub"
_ns="gnu"
_url="${_http}/${_ns}/${_pkg}"
_tarname="${_pkg}-${pkgver}"
source=(
  "${_url}/${_tarname}.tar.gz"{"",".sig"}
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
  local \
    _configure_opts=()
  _configure_opts+=(
    --prefix="/usr"
    --libexecdir="/usr/lib"
    --sysconfdir="/etc"
    --without-libsigsegv
  )
  cd \
    "${_tarname}"
  ./configure \
    "${_configure_opts[@]}"
  make
}

check() {
  cd \
    "${_tarname}"
  make check
}

package() {
  cd \
    "${_tarname}"
  make \
    DESTDIR="${pkgdir}" \
    PREFIX="/usr" \
    install
}
