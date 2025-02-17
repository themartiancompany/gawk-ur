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
    # The sources for this package have not
    # been uploaded on gnosis as
    # its too expensive for me currently but
    # on holesky.
    # For this package to be made entirely
    # undeletable the evmfs crowd-sourced
    # publishing contract will have to 
    # completed.
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
_proj="gnu"
_pkg=gawk
pkgname="${_pkg}"
pkgver=5.3.1
pkgrel=1
pkgdesc="GNU version of awk"
arch=(
  'arm'
  'aarch64'
  'pentium4'
  'i686'
  'x86_64'
)
url="https://www.${_proj}.org/software/${_pkg}"
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
_http="https://ftp.${_proj}.org/pub"
_ns="${_proj}"
_url="${_http}/${_ns}/${_pkg}"
_tarname="${_pkg}-${pkgver}"
_sig_net="100"
_sig_fs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_archive_net="17000"
_archive_fs_address="0x151920938488F193735e83e052368cD41F9d9362"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_archive_sum='fa41b3a85413af87fb5e3a7d9c8fa8d4a20728c67651185bb49c38a7f9382b1e'
_evmfs_archive_uri="evmfs://${_archive_net}/${_archive_fs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.tar.gz::${_evmfs_archive_uri}"
_archive_sig_sum="914e311fea0443b8cc3e18b8670deea2b135bb138b85f404a65aba1ee130b9ca"
_archive_sig_uri="evmfs://${_sig_net}/${_sig_fs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.tar.gz.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _src_sig="${_archive_sig_src}"
elif [[ "${_evmfs}" == "false" ]]; then
  _src="${_tarname}.tar.gz::${_url}/${_tarname}.tar.gz"
  _sig_src="${_tarname}.tar.gz.sig::${_url}/${_tarname}.tar.gz.sig"
fi
source=(
  "${_src}"
  "${_sig_src}"
)
sha256sums=(
  "${_archive_sum}"
  "${_archive_sig_sum}"
)
validpgpkeys=(
   # Arnold Robbins
  'D1967C63788713177D861ED7DF597815937EC0D2'
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
