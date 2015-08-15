# $Id: PKGBUILD 103303 2014-01-02 22:42:11Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>

pkgname=flickcurl-https
pkgver=1.25
pkgrel=1
pkgdesc="C library for the Flickr API, patched for https (should be destroyed when bug is corrected)"
arch=(i686 x86_64)
url="http://librdf.org/flickcurl/"
license=('GPL')
depends=('raptor' 'curl')
source=(http://download.dajobe.org/flickcurl/flickcurl-$pkgver.tar.gz flickcurl_https.patch)
md5sums=('9598526f2b9a0a4619d1f1563300e72a'
         '51500f8819c95a1ce95f3fae8682f43b')

build() {
  cd "$srcdir/flickcurl-$pkgver"
  sed -i 's|#include <curl/types.h>||' src/flickcurl_internal.h
  patch -p1 < ../../flickcurl_https.patch
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/flickcurl-$pkgver"
  make DESTDIR="$pkgdir/" install
}
