# Maintainer: dunningd <duncansdunning at yahoo dot co dot uk>
# Adapted/copied from netbeans-cpp 6.9.1 (Thanks wimvdh)
_pkgname=netbeans
pkgname=$_pkgname-cpp-beta
pkgver=8.0b1
pkgrel=1
pkgdesc="Netbeans IDE development platform - C/C++ only"
arch=('i686' 'x86_64')
url="http://www.netbeans.org"
license=('CDDL')
depends=('java-environment')
optdepends=('lib32-glibc')
provides=('netbeans')
conflicts=('netbeans')
options=('!strip')
install=netbeans.install
source=(http://dlc.sun.com.edgesuite.net/netbeans/8.0/beta/zip/netbeans-8.0beta-201401141042-cpp.zip netbeans.desktop netbeans.install)

md5sums=('ccc3c17da92156730f1411aeda1e3b4f'
         'd354298d6ddea111032b2cd407350130'
         '5be30146c11b754fbf62707f1e81e3a4')

build() {
    cd "$srcdir"
    
    msg2 "cleanup OS specific files"
    rm $(find -name '*\.exe' -or -name '*\.bat' -or -name '*\.dll')
    rm -r $(find -name 'MacOSX*' -or -name 'Windows*' -or -name 'SunOS*')
    rm -r $(find -name 'hpux*' -or -name 'mac*' -or -name 'solaris*' -or -name 'windows*')
}                    

package() {
  cd $srcdir
  mkdir -p $pkgdir/usr/share/netbeans

  cp -r $srcdir/netbeans/* $pkgdir/usr/share/netbeans/

  install -Dm644 $srcdir/netbeans.desktop $pkgdir/usr/share/applications/netbeans.desktop
  install -Dm644 $srcdir/netbeans/nb/netbeans.png $pkgdir/usr/share/pixmaps/netbeans.png
  mkdir -p $pkgdir/usr/bin
  ln -s /usr/share/netbeans/bin/netbeans $pkgdir/usr/bin/netbeans
  install -Dm644 $srcdir/netbeans/LICENSE.txt $pkgdir/usr/share/licenses/netbeans/LICENSE
}
