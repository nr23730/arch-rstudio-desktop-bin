# Maintainer: Meow

pkgname=rstudio-desktop-bin
pkgver=2023.12.1.402
_pkgver=2023.12.1-402
pkgrel=1
pkgdesc="An integrated development environment (IDE) for R (binary from RStudio official repository)"
arch=('x86_64')
license=('GPL')
url="http://www.rstudio.org/"
depends=('r>=3.3.0' 'clang' 'libxkbcommon-x11' 'sqlite')
makedepends=()
optdepends=('clang: C/C++ and Rcpp support')
conflicts=('rstudio-desktop' 'rstudio-desktop-git' 'rstudio-desktop-preview-bin')
provides=("rstudio-desktop=${pkgver}")
options=(!strip)

sha256sums_x86_64=(
75542cc24c59404f8d62815bc0e31b43032b5032e651fa9f618dbcdca8aa7cac
)

source_x86_64=("https://download1.rstudio.org/electron/jammy/amd64/rstudio-${_pkgver}-amd64.deb")

install="$pkgname".install

package() {

  shopt -s extglob

  msg "Converting debian package..."

  cd "$srcdir"
  tar Jxpf data.tar.xz -C "$pkgdir"

  install -dm755 "$pkgdir/usr/bin"

  ln -s /usr/lib/rstudio/rstudio "$pkgdir/usr/bin/rstudio"

  sed -i 's/rstudio\/rstudio/rstudio\/rstudio --ozone-platform-hint=auto --enable-features=WaylandWindowDecorations /g' "$pkgdir/usr/share/applications/rstudio.desktop"

}
# vim:ft=sh tabstop=2 expandtab
