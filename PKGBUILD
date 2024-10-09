# Maintainer: Your Name <youremail@example.com>
pkgname=natio
pkgver=0.1
pkgrel=1
pkgdesc="A simple CLI application"
arch=('x86_64')
url="https://github.com/focando0/natio"
license=('MIT')
depends=('python')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('SKIP')

package() {
    cd "$srcdir/$pkgname-$pkgver"
    
    # Install the script
    install -Dm755 myapp.py "$pkgdir/usr/bin/natio"
}

