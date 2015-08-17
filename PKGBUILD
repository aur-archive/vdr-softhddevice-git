# Maintainer: David Spicer <azleifel at gmail dot com>

pkgname=vdr-softhddevice-git
_gitname=vdr-plugin-softhddevice
pkgver=20140114
pkgrel=1
pkgdesc="A software and GPU emulated HD output device plugin for VDR"
arch=('i686' 'x86_64')
url="http://projects.vdr-developer.org/projects/plg-softhddevice"
license=('AGPL3')
depends=('ffmpeg' 'ffmpeg-compat' 'vdr>=2.0.0' 'xcb-util-wm')
makedepends=('xcb-util' 'xcb-util-keysyms')
optdepends=('libva-intel-driver: Intel integrated graphics backend for VA-API'
            'libva-vdpau-driver: VDPAU backend for VA-API'
            'xvba-video-open: XVBA backend for VA-API')
provides=('vdr-softhddevice')
conflicts=('vdr-softhddevice')
source=('git://projects.vdr-developer.org/vdr-plugin-softhddevice.git')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_gitname"
  git log -1 --format="%cd" --date=short | sed 's|-||g'
}

build() {
  cd "$srcdir/$_gitname"

  make
}

package() {
  cd "$srcdir/$_gitname"

  make DESTDIR="$pkgdir/" install

  # Install documents
  install -d -m755 "$pkgdir/usr/share/doc/$pkgname"
  for _file in README.txt ChangeLog; do
    install -m644 $_file "$pkgdir/usr/share/doc/$pkgname"
  done
}
