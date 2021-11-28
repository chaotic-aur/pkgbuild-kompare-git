# Merged with official ABS kompare PKGBUILD by João, 2021/04/24 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Sándor Nagy <sanya868 at gmail dot com>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=kompare-git
pkgver=21.07.70_r1096.gb136844
pkgrel=1
pkgdesc='Graphical file differences tool'
url='https://apps.kde.org/kompare/'
arch=($CARCH)
license=(GPL LGPL FDL)
groups=(kde-applications-git kdesdk-git)
depends=(libkomparediff2-git ktexteditor-git hicolor-icon-theme)
makedepends=(git extra-cmake-modules-git kdoctools-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _major_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MAJOR' CMakeLists.txt | cut -d '"' -f2)"
  _minor_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MINOR' CMakeLists.txt | cut -d '"' -f2)"
  _micro_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MICRO' CMakeLists.txt | cut -d '"' -f2)"
  echo "${_major_ver}.${_minor_ver}.${_micro_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
