# Maintainer: Jan de Groot <jgc@archlinux.org>
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Douglas Soares de Andrade <dsa@aur.archlinux.org>
# Contributor: Angel 'angvp' Velasquez <angvp[at]archlinux.com.ve> 

pkgname=python-umap
pkgver=0.4.3
pkgrel=0
pkgdesc=""
arch=('x86_64')
license=('custom')
url=""
depends=('intel-tbb' 'python-numpy' 'python-scipy' 'python-scikit-learn' 'python-numba')
makedepends=('python-setuptools')
source=("$pkgname-$pkgver.tar.gz::https://github.com/lmcinnes/umap/archive/$pkgver.tar.gz")
sha512sums=('SKIP')

build() {
  cd umap-$pkgver
  python setup.py build
}


package() {
  cd umap-$pkgver
  python setup.py install --prefix=/usr --root="${pkgdir}" --optimize=1

  install -m755 -d "${pkgdir}/usr/share/licenses/python-umap"
  install -m644 LICENSE.txt "${pkgdir}/usr/share/licenses/python-umap/"
}
