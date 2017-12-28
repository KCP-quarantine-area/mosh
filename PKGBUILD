pkgname=mosh
pkgver=1.3.2
pkgrel=1
pkgdesc='Mobile shell, surviving disconnects with local echo and line editing'
arch=('x86_64')
url='https://mosh.org/'
license=('GPL3')
depends=('libutempter' 'perl-io-tty' 'protobuf')
makedepends=('git')
options=('!emptydirs')
source=("git+https://github.com/mobile-shell/mosh#tag=$pkgname-$pkgver")
sha512sums=('SKIP')

build() {
  cd "$pkgname"

  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  make -C "$pkgname" DESTDIR="$pkgdir" install

  install -Dm644 "$pkgname/conf/bash-completion/completions/$pkgname" \
    "$pkgdir/usr/share/bash-completion/completions/$pkgname"
}
