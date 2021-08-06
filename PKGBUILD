# Maintainer: Patrick Goetz <pgoetz at mail dot utexas dot edu>
# Contributor: Doug Newgard <scimmia at archlinux dot org>
# Contributor: Jiachen Yang <farseerfc@gmail.com>
# Contributor: Miguel Revilla <yo@miguelrevilla.com>
# Contributor: Ferik <djferik at gmail dot com>

pkgname=masterpdfeditor
pkgver=5.6.80
pkgrel=1
epoch=100
pkgdesc='A complete solution for viewing, creating and editing PDF files'
url='https://code-industry.net/free-pdf-editor/'
arch=('x86_64')
license=('custom')
makedepends=('patchelf')
source_x86_64=('master-pdf-editor-5.6.80-qt5.x86_64.tar.gz'
               'masterpdfeditor5.desktop')
sha256sums_x86_64=('9fbda562095ddaca973af73aaefd51f8e46dc30e215469bb5183958a60dae207'
                   'fa380da45926166ba8fe474276fe309eeae7187906f5e2c1e0f18a8863af6b1a')

package() {
  depends=('libgl' 'nspr' 'nss' 'qt5-base' 'qt5-svg' 'sane' 'util-linux')

  install -d "$pkgdir"{/opt/,/usr/bin/}
  cp -a --no-preserve=ownership master-pdf-editor-${pkgver%%.*} "$pkgdir/opt/"

  cd "$pkgdir/opt/master-pdf-editor-${pkgver%%.*}"
  ln -sr masterpdfeditor${pkgver%%.*} -t "$pkgdir/usr/bin/"
  install -Dm644 ${srcdir}/masterpdfeditor${pkgver%%.*}.desktop -t "$pkgdir/usr/share/applications/"
  install -Dm644 license.txt -t "$pkgdir/usr/share/licenses/$pkgname/"
  patchelf --remove-rpath masterpdfeditor${pkgver%%.*}
}
