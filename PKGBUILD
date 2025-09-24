pkgname=qt6-qt5compat
pkgver=6.9.2
pkgrel=1
pkgdesc="Module that contains unsupported Qt 5 APIs"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'icu'
    'qt6-qtbase'
    'qt6-qtshadertools'
)
makedepends=(
    'cmake'
    'ninja'
    'qt6-qtdeclarative'
)
source=(https://download.qt.io/archive/qt/${pkgver%.*}/${pkgver}/submodules/${pkgname#*-}-everywhere-src-${pkgver}.tar.xz)
sha256sums=(cb289905c689fc271ce783f8b67844040aa73d78f4f0cf8421fa713390a75b60)

build() {
    cd ${pkgname#*-}-everywhere-src-${pkgver}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build

}

package() {
    cd ${pkgname#*-}-everywhere-src-${pkgver}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
