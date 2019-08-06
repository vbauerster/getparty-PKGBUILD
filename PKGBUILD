# Maintainer: Vladimir Bauer <vbauerster@gmail.com>
pkgname=getparty
pkgver=1.7.2
pkgrel=1
pkgdesc="HTTP Download Manager with multi-parts"
arch=('i686' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://github.com/vbauerster/$pkgname"
license=('BSD')
makedepends=(
  'go'
  'git'
)
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha1sums=('1cba740cfd736a738d704c30f0eee72c9b54ad84')

build() {
    local commit=$(git ls-remote --tags $url | grep -F $pkgver)
    cd "$pkgname-$pkgver/cmd/$pkgname"
    go build \
        -gcflags "all=-trimpath=$PWD" \
        -asmflags "all=-trimpath=$PWD" \
        -ldflags="-X main.version=$pkgver -X main.commit=${commit:0:7}" \
        .
}

package() {
    cd $pkgname-$pkgver
    install -Dm755 "cmd/$pkgname/$pkgname" "$pkgdir/usr/bin/$pkgname"
}
