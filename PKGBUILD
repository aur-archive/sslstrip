# Maintainer: Levente Polyak <levente[at]leventepolyak[dot]net>
# Contributor: Jonas Heinrich <onny@project-insanity.org>
# Contributor: MatToufoutu <mattoufootu[at]gmail.com>

pkgname=sslstrip
pkgver=0.9
pkgrel=6
pkgdesc="Python tool to hijack HTTPS connections during a MITM attack"
url="http://www.thoughtcrime.org/software/sslstrip/"
arch=('any')
license=('GPL3')
depends=('python2-pyopenssl' 'python2-twisted' 'python2-service-identity')
source=(http://www.thoughtcrime.org/software/sslstrip/${pkgname}-${pkgver}.tar.gz)
sha512sums=("f6e24db0dcb0c4e137b5828d043db17f5d59e46181f51b1814cf66466b55d6a11a95e7ee8748e59faacfc6176689d030af5fa5c99dedce47e8f9ca6cc7316abc")

prepare() {
  cd ${pkgname}-${pkgver}
  sed -e 's/env python$/env python2/g' -i sslstrip.py
  # package data files ourselves to match arch structure
  sed -e '/data_files = /d' -i setup.py
}

package() {
  cd ${pkgname}-${pkgver}
  python2 setup.py install -O1 --root="${pkgdir}" --prefix=/usr
  install -Dm 644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
  install -Dm 644 lock.ico "${pkgdir}/usr/share/${pkgname}/lock.ico"
}

# vim: ts=2 sw=2 et:
