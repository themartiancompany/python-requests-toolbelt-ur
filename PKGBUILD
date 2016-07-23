# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: eolianoe <eolianoe At GoogleMAIL DoT com>

pkgbase=python-requests-toolbelt
pkgname=('python-requests-toolbelt' 'python2-requests-toolbelt')
pkgver=0.7.0
pkgrel=1
pkgdesc="A toolbelt of useful classes and functions to be used with python-requests."
arch=('any')
url="https://github.com/sigmavirus24/requests-toolbelt"
license=('Apache')
makedepends=('python-setuptools' 'python2-setuptools' 'python-requests' 'python2-requests' 'git')
checkdepends=('python-pytest' 'python2-pytest' 'python-betamax' 'python2-betamax'
              'python-mock' 'python2-mock')
source=("git+https://github.com/sigmavirus24/requests-toolbelt.git#tag=$pkgver")
md5sums=('SKIP')

prepare() {
  cp -a requests-toolbelt{,-py2}
}

build() {
  cd "$srcdir"/requests-toolbelt
  python setup.py build

  cd "$srcdir"/requests-toolbelt-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/requests-toolbelt
  py.test

  cd "$srcdir"/requests-toolbelt-py2
  py.test2
}

package_python-requests-toolbelt() {
  depends=('python-requests')

  cd requests-toolbelt
  python setup.py install --root="$pkgdir" --optimize=1
}

package_python2-requests-toolbelt() {
  depends=('python2-requests')

  cd requests-toolbelt-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
}
