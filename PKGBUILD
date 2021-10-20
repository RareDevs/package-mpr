# AUR-Maintaner: Dummerle
# Maintainer: zocker_160 <zocker1600 at posteo dot net>

pkgname=rare
pkgver=1.6.2
pkgrel=1
pkgdesc="A GUI for legendary, an open source replacement for Epic Games Launcher"
arch=('any')
url="https://github.com/Dummerle/Rare"
license=('GPL3')
depends=("python3-wheel" "python3-setuptools" "python3-pyqt5" "python3-qtawesome" "python3-requests" "python3-pil" "python3-psutil" "python3-pypresence")
makedepends=("git" "python3-setuptools" "gendesk")
optdepends=("wine-staging: Run windows games")
provides=('rare')
conflicts=('rare-git')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/$pkgver.tar.gz")
sha256sums=("e63ae0f57df5d46efca127bc1da46716e8842e85233dd52a981d82e3d43aaf29")

prepare() {
    cd "$srcdir/Rare-$pkgver"
    cp $srcdir/Rare-$pkgver/rare/resources/images/Rare.png $srcdir/Rare-$pkgver/$pkgname.png
    sed -i 's/mdi.view-grid-outline/mdi.view-grid/' $srcdir/Rare-$pkgver/rare/utils/extra_widgets.py
    gendesk -f -n \
    --pkgname "$pkgname" \
    --pkgdesc "$pkgdesc" \
    --categories "Application;Game;Launcher" \
    --custom "Keywords=epic;games;launcher;legendary;"
}

build() {
    cd "$srcdir/Rare-$pkgver"
    python3 setup.py build
}

package() {
    cd "$srcdir/Rare-$pkgver"
    python3 setup.py install --root="$pkgdir/" --optimize=1 --skip-build
    install -Dm644 "${pkgname}.desktop" "$pkgdir/usr/share/applications/${pkgname}.desktop"
    install -Dm644 "${pkgname}.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
}

