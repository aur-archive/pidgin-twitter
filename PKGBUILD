# Maintainer : speps <speps at aur dot archlinux dot org>
# Contributor: Sigitas Mazaliauskas <sigisnn at gmail dot com>

pkgname=pidgin-twitter
pkgver=0.9.2.1
pkgrel=2
pkgdesc="Pidgin plugin for Twitter support"
arch=('i686' 'x86_64')
url="http://honeyplanet.jp/pidgin-twitter"
license=('GPL')
depends=('pidgin')
source=("http://www.honeyplanet.jp/$pkgname-$pkgver.tar.gz")
md5sums=('392166bf14bda1272052d61c72e11ddf')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"

  # glib2 fixes
  sed -i 's/gdk_pixbuf_unref/g_object_unref/' icon.c
  sed -i '/g_type_init/d' main.c
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  # lib
  install -Dm755 $pkgname.so \
    "$pkgdir/usr/lib/pidgin/$pkgname.so"

  # conf
  install -Dm644 prefs.ui \
    "$pkgdir/usr/share/$pkgname/prefs.ui"
}