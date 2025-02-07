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
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
_solc="true"
_hardhat="true"
_pkg=solidity-compiler
pkgname="${_pkg}"
pkgver="0.0.0.0.0.0.0.0.0.0.0.1.1.1.1.1.1.1.1"
_commit="63bf12ca1fa14b91d2cdb9f362c730622b8d402f"
pkgrel=1
_pkgdesc=(
  "Solidity compiler supporting multiple backends."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
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
_os="$( \
  uname \
    -o)"
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
optdepends+=(
  "solidity<ver>: support for solc version <ver> in the correspondent backend"
)
makedepends=(
  make
)
checkdepends=(
  "shellcheck"
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
if [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum='ffb9069507bf5ea97a10496f630aa46c6b8efe3d54ef87f9a234226d5df68aae'
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
