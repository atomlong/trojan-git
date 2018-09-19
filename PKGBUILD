# Maintainer: Ariel AxionL <axionl@aosc.io>
# Contributor: GreaterFire <GreaterFire@protonmail.com>
pkgname=trojan-git
pkgver=r295.4a6b846
pkgrel=1
pkgdesc="An unidentifiable mechanism that helps you bypass GFW"
arch=('x86_64')
url="https://github.com/trojan-gfw/trojan"
license=('GPL3')
depends=('boost-libs' 'openssl' 'libmariadbclient')
optdepends=('ca-certificates: server certificate verification'
            'mariadb: advanced user management')
makedepends=('git' 'cmake' 'boost' 'openssl' 'libmariadbclient')
checkdepends=('openssl' 'python' 'curl')
conflicts=('trojan')
provides=('trojan')
source=("$pkgname::git+$url")
backup=('etc/trojan/config.json')
sha512sums=('SKIP')

pkgver() {
    cd "$srcdir/$pkgname"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd $pkgname
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr .
    make
}

check() {
    cd $pkgname
    ctest
}

package() {
    cd $pkgname
    make DESTDIR=$pkgdir install
}
# vim set: ts=4 sw=4 et
