pkgname=qt6-qt5compat
pkgver=6.10.0
pkgrel=2
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
    'git'
    'ninja'
    'qt6-qtdeclarative'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(b99e86ed67aa627d77c184db279968fe3a2c4e46633ffff3461afb80c9c5ef2f)

build() {
    cd ${pkgname#*-}

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
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
