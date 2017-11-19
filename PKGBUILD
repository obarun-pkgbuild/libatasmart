# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/libatasmart
# 						Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=libatasmart
pkgver=0.19
pkgrel=3
pkgdesc="ATA S.M.A.R.T. Reading and Parsing Library"
arch=('x86_64')
license=('LGPL')
url="http://0pointer.de/blog/projects/being-smart.html"
source=(http://0pointer.de/public/${pkgname}-${pkgver}.tar.xz
        0001-Dont-test-undefined-bits.patch
        0002-Drop-our-own-many-bad-sectors-heuristic.patch)
md5sums=('53afe2b155c36f658e121fe6def33e77'
         'eb5d0468b0d47d099e5164372a21f9da'
         'cebd1fbed0b05d0458177d6d3ad4ea3f')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

prepare() {
  cd ${pkgname}-$pkgver
  patch -Np1 -i ../0001-Dont-test-undefined-bits.patch
  patch -Np1 -i ../0002-Drop-our-own-many-bad-sectors-heuristic.patch
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --sbindir=/usr/bin \
    --disable-static
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
