# Maintainer: Dummerle
# Maintainer: zocker_160 <zocker1600 at posteo dot net>

pkgname=rare
pkgver=1.10.11.525
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
sha256sums=('5571dce60d9dfca6f58c678a31a8e24425b3cb64e7184a8451a0fdcf47702f1f')

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

