# Maintainer: Dummerle
# Maintainer: zocker_160 <zocker1600 at posteo dot net>

pkgname=rare
pkgver=1.10.6
pkgrel=1
pkgdesc="A GUI for legendary, an open source replacement for Epic Games Launcher"
arch=('any')
url="https://github.com/RareDevs/Rare"
license=('GPL3')
depends=(
  python3-wheel
  python3-pyqt5
  python3-pyqt5.qtsvg
  python3-qtawesome
  python3-requests
  python3-typing-extensions
  legendary
)
makedepends=(
  git
  python3-setuptools
)
optdepends=(
  "wine: run Windows games"
  "python3-pypresence: Discord RPC integration"
  "python3-webview: embedded browser for logging in"
)
source=("git+https://github.com/RareDevs/Rare.git#tag=$pkgver")
sha256sums=("SKIP")

build() {
  cd Rare
  python3 setup.py build
}

package() {
  cd Rare
  python3 setup.py install --prefix=/usr --install-layout=deb --root="$pkgdir/" --optimize=1 --skip-build
  install -Dm644 "misc/${pkgname%-git}.desktop" "$pkgdir/usr/share/applications/${pkgname%-git}.desktop"
  install -Dm644 "rare/resources/images/Rare.png" "$pkgdir/usr/share/pixmaps/${pkgname%-git}.png"
}
