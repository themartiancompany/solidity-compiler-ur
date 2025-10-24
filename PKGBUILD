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

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

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
if [[ ! -v "_offline" ]]; then
  _offline="true"
fi
if [[ ! -v "_offline" ]]; then
  _git="false"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="gitlab"
fi
if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
if [[ ! -v "_archive_format" ]]; then
  _archive_format="tar.gz"
  if [[ "${_git_http}" == "github" ]]; then
    _archive_format="zip"
  fi
fi
_solc="true"
_hardhat="true"
_py="python"
_pkg=solidity-compiler
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}"
  )
fi
pkgver="0.0.0.0.0.0.0.0.0.0.1.1"
_commit="7d03014fedb66944a4b352c039e0397d03235da3"
pkgrel=1
_pkgdesc=(
  "Solidity compiler supporting multiple backends."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  'AGPL3'
)
depends=(
  "libcrash-bash"
  "sed"
)
optdepends=()
if [[ "${_hardhat}" == "true" ]]; then
  depends+=(
    "indent"
    "solidity-analyzer"
    "hardhat"
  )
  if [[ "${_os}" == "GNU/Linux" ]] && \
     [[ "${_os}" != "Android" ]]; then
    depends+=(
      'findutils'
      'cpio'
      'eslint-plugin-hardhat-internal-rules'
      'eslint-plugin-slow-imports'
    )
  fi
elif [[ "${_hardhat}" == "false" ]]; then
  optdepends+=(
    "hardhat: hardhat backend support"
  )
fi
if [[ "${_solc}" == "true" ]]; then
  depends+=(
    "solidity"
  )
elif [[ "${_solc}" == "false" ]]; then
  optdepends+=(
    "solidity: solc backend support"
  )
fi
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
  )
  optdepends+=(
  )
fi
_solidity_optdepends=(
  "solidityX.Y.Z:"
    "support for solc version X.Y.Z in the correspondent backend."
)
optdepends+=(
  "${_solidity_optdepends[*]}"
)
makedepends=(
  'make'
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
checkdepends=(
  "shellcheck"
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${_pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_sum="9764e8d75cd5f94298c40aa828d0b2c8408def3d922064f03898b4033ba5192e"
_sig_sum="cf9ffff10b05bd3dd9a04ea94664bda7b7dc0be6ff7b765a3f3165d04f5cfe7c"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_src}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _uri="git+${_url}#${_tag_name}=${_tag}?signed"
  _src="${_tarname}::${_uri}"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _uri="${_url}/archive/refs/tags/${_tag}.${_archive_format}"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _uri="${_url}/archive/${_commit}.zip"
  fi
  _src="${_tarfile}::${_uri}"
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package_solidity-compiler() {
  local \
    _make_opts=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  install \
    -Dm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_solidity-compiler-docs() {
  local \
    _make_opts=()
  depends=()
  _make_opts+=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-doc
  make \
    "${_make_opts[@]}" \
    install-man
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim: ft=sh syn=sh et
