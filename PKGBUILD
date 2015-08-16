# Contributor: Alexander Rødseth <rodseth@gmail.com>
# Contributor: Shinlun Hsieh <yngwiexx@yahoo.com.tw>
# Contributor: Alex Ghoust <ghoust@skyper.homelinux.org>
pkgname=mingw32-libsigcpp1.2
pkgver=1.2.7
pkgrel=1
pkgdesc="A typesafe callback system for standard C++ (mingw32)"
arch=('i686' 'x86_64')
url="http://libsigc.sourceforge.net/"
license=('LGPL')
depends=('glibc')
makedepends=('setconf')
source=(http://ftp.gnome.org/pub/GNOME/sources/libsigc++/1.2/libsigc++-$pkgver.tar.bz2)
md5sums=('212f48536019e1f003d2509b4c9b36df')

build() {
  _target=i486-mingw32
  cd "$srcdir/libsigc++-$pkgver"
  unset LDFLAGS
  ./configure --prefix=/usr/${_target} --build=$CHOST --host=${_target} || return 1
  setconf Makefile SUBDIRS "sigc++ doc"
  make || return 1
  make DESTDIR="$pkgdir/" install || return 1
  find "$pkgdir" -name "*.la" -exec rm {} +
  install -Dm644 COPYING $pkgdir/usr/i486-mingw32/share/licenses/$pkgname/COPYING
}

# vim:set ts=2 sw=2 et:
