# Maintainer: Vladimir Bauer <vbauerster@gmail.com>
pkgname=getparty
pkgver=1.7.2
pkgrel=1
pkgdesc="HTTP Download Manager with multi-parts."
arch=('i686' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://github.com/vbauerster/getparty"
license=('BSD')
depends=(
  'pacman>=5.1'
  'sudo'
  'git'
)
makedepends=(
  'go'
)
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/vbauerster/getparty/archive/v${pkgver}.tar.gz")
sha1sums=('1cba740cfd736a738d704c30f0eee72c9b54ad84')

build() {
    local commit=$(git ls-remote --tags https://github.com/vbauerster/getparty | grep -F $pkgver | cut -f1)
    cd "$srcdir/$pkgname-$pkgver/cmd/getparty"
    go build -ldflags="-X main.version=$pkgver -X main.commit=$commit"
}

package() {
    install -Dm755 "$srcdir/$pkgname-$pkgver/cmd/getparty/getparty" "$pkgdir/usr/bin/getparty"
}
