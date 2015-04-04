# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: eolianoe <eolianoe At GoogleMAIL DoT com>

pkgbase=python-requests-toolbelt
pkgname=('python-requests-toolbelt' 'python2-requests-toolbelt')
_pkgname=requests-toolbelt
pkgver=0.4.0
pkgrel=1
pkgdesc="A toolbelt of useful classes and functions to be used with python-requests."
arch=('any')
url="https://github.com/sigmavirus24/requests-toolbelt"
license=('Apache')
makedepends=('python-setuptools' 'python2-setuptools' 'python-requests' 'python2-requests')
checkdepends=('python-pytest' 'python2-pytest')
source=("https://pypi.python.org/packages/source/r/${_pkgname}/${_pkgname}-${pkgver}.tar.gz")
md5sums=('2278d650faadf181dd180682591e5926')

prepare() {
  cp -a ${_pkgname}-$pkgver{,-py2}
}

build() {
  cd "$srcdir/${_pkgname}-$pkgver"
  python setup.py build

  cd "$srcdir/${_pkgname}-$pkgver-py2"
  python2 setup.py build
}

check() {
  # Tests not included
  cd "$srcdir/${_pkgname}-$pkgver"
  py.test

  cd "$srcdir/${_pkgname}-$pkgver-py2"
  py.test2
}

package_python-requests-toolbelt() {
  depends=('python-requests')

  cd "$srcdir/${_pkgname}-$pkgver"
  python setup.py install --root="$pkgdir/" --optimize=1
}

package_python2-requests-toolbelt() {
  depends=('python2-requests')

  cd "$srcdir/${_pkgname}-$pkgver-py2"
  python2 setup.py install --root="$pkgdir/" --optimize=1
}
