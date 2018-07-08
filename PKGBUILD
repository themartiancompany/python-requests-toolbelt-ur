# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: eolianoe <eolianoe At GoogleMAIL DoT com>

pkgbase=python-requests-toolbelt
pkgname=('python-requests-toolbelt' 'python2-requests-toolbelt')
pkgver=0.8.0
pkgrel=3
pkgdesc="A toolbelt of useful classes and functions to be used with python-requests."
arch=('any')
url="https://github.com/requests/toolbelt"
license=('Apache')
makedepends=('python-setuptools' 'python2-setuptools' 'python-requests' 'python2-requests')
checkdepends=('python-pytest' 'python2-pytest' 'python-betamax' 'python2-betamax'
              'python-mock' 'python2-mock')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/requests/toolbelt/archive/$pkgver.tar.gz")
sha512sums=('55bf93d386442f5deb81eabd85812ffd49e98ff88c0bb96e15271efd84deb7c5d854a2cdc81c989a7d74870e8a218fc968d080052d9ca7cd9733a2378ea9c2f5')

prepare() {
  cp -a toolbelt-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/toolbelt-$pkgver
  python setup.py build

  cd "$srcdir"/toolbelt-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/toolbelt-$pkgver
  py.test

  cd "$srcdir"/toolbelt-$pkgver-py2
  py.test2
}

package_python-requests-toolbelt() {
  depends=('python-requests')

  cd toolbelt-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
}

package_python2-requests-toolbelt() {
  depends=('python2-requests')

  cd toolbelt-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
}
