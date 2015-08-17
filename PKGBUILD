pkgname=qjson-git
pkgver=20130302
pkgrel=1
pkgdesc="A qt-based library that maps JSON data to QVariant objects"
arch=('i686' 'x86_64')
license=('GPL')
url="http://qjson.sourceforge.net"
depends=('qt4')
makedepends=('cmake' 'git')
conflicts=('qjson')
provides=('qjson')

_gitroot="https://github.com/flavio/qjson.git"
_gitname="qjson"

build() {
  cd $srcdir
  msg "Connecting to the GIT server...."
  
  if [[ -d $srcdir/$_gitname ]] ; then
    cd $_gitname
    git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi
  
  msg "GIT checkout done"
  msg "Starting make..."
  
  mkdir $srcdir/$_gitname-build
 
  cd $srcdir/$_gitname-build

  cmake $startdir/src/$_gitname -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release
}

package() {
  cd ${srcdir}/$_gitname-build
  make DESTDIR=${pkgdir} install
  rm -r $srcdir/$_gitname-build
}
