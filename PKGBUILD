# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: eolianoe <eolianoe At GoogleMAIL DoT com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_proj="requests"
_Pkg="toolbelt"
_pkg="${_proj}-${_Pkg}"
_pkgname="${_pkg}"
pkgname="${_py}-${_pkg}"
pkgver=1.0.0
pkgrel=2
_pkgdesc=(
  "A toolbelt of useful classes"
  "and functions to be used with"
  "python-requests."
)
arch=(
  'any'
)
_http="https://github.com"
_ns="${_proj}"
url="${_http}/${_ns}/${_Pkg}"
license=(
  'Apache'
)
depends=(
  "${_py}-requests"
)
makedepends=(
  "${_py}-setuptools"
)
checkdepends=(
  'python-pytest'
  'python-betamax'
  'python-ndg-httpsclient'
  'python-pyopenssl'
  'python-trustme'
)
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/${pkgver}.tar.gz"
)
sha512sums=(
  '1ee5d5dbb0d140796c81d42c051ccfab8810bf5ec511b32c9a54b4adccbab460f3108acdfe5a65b3cb68377586ff0f55206bf231e64651aaea077feda7984953'
)

build() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_Pkg}-${pkgver}"
  pytest
}

package() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
      --root="${pkgdir}" \
      --optimize=1
}
