# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: eolianoe <eolianoe At GoogleMAIL DoT com>

pkgbase=python-requests-toolbelt
pkgname=('python-requests-toolbelt' 'python2-requests-toolbelt')
pkgver=0.8.0
pkgrel=1
pkgdesc="A toolbelt of useful classes and functions to be used with python-requests."
arch=('any')
url="https://github.com/sigmavirus24/requests-toolbelt"
license=('Apache')
makedepends=('python-setuptools' 'python2-setuptools' 'python-requests' 'python2-requests')
checkdepends=('python-pytest' 'python2-pytest' 'python-betamax' 'python2-betamax'
              'python-mock' 'python2-mock')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/sigmavirus24/requests-toolbelt/archive/$pkgver.tar.gz")
sha512sums=('902114a1e3a8d67d789ebf652bc68477b31d3b5f9e36b44bdbe9dc56f981a30083f53179f6539f68014e12962deb8599a86ee806a3c2d8f633725d4cbbfa61cd')

prepare() {
  cp -a requests-toolbelt-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/requests-toolbelt-$pkgver
  python setup.py build

  cd "$srcdir"/requests-toolbelt-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/requests-toolbelt-$pkgver
  py.test

  cd "$srcdir"/requests-toolbelt-$pkgver-py2
  py.test2
}

package_python-requests-toolbelt() {
  depends=('python-requests')

  cd requests-toolbelt-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
}

package_python2-requests-toolbelt() {
  depends=('python2-requests')

  cd requests-toolbelt-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
}
