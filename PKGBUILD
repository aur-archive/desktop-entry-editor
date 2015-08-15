# Maintainer: Julien Nicoulaud <julien.nicoulaud@gmail.com>
# Source: https://github.com/nicoulaj/archlinux-packages
pkgname=desktop-entry-editor
pkgver=0.1.1
pkgrel=4
pkgdesc="A Desktop Entry editor based on the freedesktop.org specifications."
arch=(any)
url="https://github.com/MicahCarrick/desktop-entry-editor"
license=(GPL)
depends=(python2 gtk3 python2-xdg python2-gobject gtksourceview3 hicolor-icon-theme intltool desktop-file-utils)
install=${pkgname}.install
changelog=Changelog
source=("https://github.com/downloads/MicahCarrick/${pkgname}/${pkgname}-${pkgver}.tar.gz")
md5sums=('626b6dd4fbf555e34dc8fdc5d194bbf7')

# NOTE This package uses Python2 because there is no pyxdg python 3 package.

build() {
  msg2 "Build..."
  cd "${srcdir}/${pkgname}-${pkgver}"
  PYTHON=python2 ./configure --prefix=/usr
  make || return 1

  msg2 "Fix Python script shebang..."
  sed -i '1s/python/python2/' "${srcdir}/${pkgname}-${pkgver}/src/${pkgname}"
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}/" install
}

# vim:set ts=2 sw=2 et:
