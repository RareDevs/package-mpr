# Maintainer: Dummerle
# Maintainer: zocker_160 <zocker1600 at posteo dot net>

pkgname=rare
pkgver=1.11.2
pkgrel=1
pkgdesc="Open source alternative for Epic Games Launcher, using Legendary"
arch=('any')
url="https://github.com/RareDevs/Rare"
license=('GPL3')
depends=(
  python3-pyside6
  python3-requests
  python3-qtawesome
  python3-orjson
  python3-vdf
  legendary
)
makedepends=(
  git
  python3-{build,installer,wheel}
  python3-setuptools{,-scm}
)
optdepends=(
  "wine: run Windows games"
  "python3-pypresence: Discord RPC integration"
  "python3-webview: embedded browser for logging in"
)
source=("git+https://github.com/RareDevs/Rare.git#tag=$pkgver")
sha256sums=('64d8f9c0f0c9291ca10a5d40bcd96c39f03b1e650f216edbe212d977de078edc')

build() {
  cd Rare
  python setup.py bdist_wheel
}

package() {
  cd Rare
  python -m installer -d "$pkgdir" dist/*.whl
  install -Dm644 "misc/${pkgname%-git}.desktop" "$pkgdir/usr/share/applications/${pkgname%-git}.desktop"
  install -Dm644 "rare/resources/images/Rare.png" "$pkgdir/usr/share/pixmaps/${pkgname%-git}.png"
}

