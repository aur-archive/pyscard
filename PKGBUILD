# Contributor: Guenther Starnberger <gst@sysfrog.org>
# Maintainer:  Artiom Molchanov <ar.molchanov@gmail.com>

pkgname=pyscard
pkgver=1.6.16
pkgrel=1
pkgdesc="pyscard is a Python module adding smart cards support to Python"
arch=('i686' 'x86_64')
url="http://pyscard.sourceforge.net/"
license='LGPL'
depends=('python2' 'pcsclite')
makedepends=('swig')
source=()
md5sums=()

_svnurl=https://pyscard.svn.sourceforge.net/svnroot/pyscard
_svn_ver=612

build() {
  cd "$srcdir"

  if [ -d $pkgname/.svn ]; then
    (cd $pkgname && svn up -r $_svn_ver)
  else
    svn co $_svnurl --config-dir ./ -r $_svn_ver $pkgname
  fi

  msg "SVN checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$pkgname-build"
  cp -r "$srcdir/$pkgname" "$srcdir/$pkgname-build"
  cd "$srcdir/$pkgname-build/trunk/$pkgname/src"

  python2 setup.py build_ext
}

package() {
  cd "$srcdir/$pkgname-build/trunk/$pkgname/src"
  python2 setup.py install --prefix=$pkgdir/usr
}
