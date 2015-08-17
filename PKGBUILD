# Maintainer: Beej Jorgensen <beej@beej.us>
pkgname=therion
pkgver=5.3.15
pkgrel=2
pkgdesc="Cave map rendering software"
arch=('i686' 'x86_64')
url="http://therion.speleo.sk/"
license=('GPL')
depends=('webkitgtk2' 'wxgtk' 'texlive-core' 'texlive-langcyrillic' 'bwidget' 'tkimg' 'vtk<6')
makedepends=()
backup=('etc/therion/therion.ini' 'etc/therion/xtherion.ini')
source=(http://therion.speleo.sk/downloads/$pkgname-$pkgver.tar.gz
        "${pkgname}_${pkgver}_aur.patch")
    
md5sums=('2dedb25f4d38f0f53144953d6cf911fb'
         '5f84a0823d8704e01cf6522ce539e0e0')

prepare() {
  cd "$pkgname"

  # AUR-specific patches
  patch -Np1 < $srcdir/${pkgname}_${pkgver}_aur.patch
}

build() {
  cd "$pkgname"

  make
}

package() {
  cd "$pkgname"

  # install rules from makeinstall.tcl
  install -m755 -D therion ${pkgdir}/usr/bin/therion
  install -m755 -D xtherion/xtherion ${pkgdir}/usr/bin/xtherion
  install -m755 -D loch/loch ${pkgdir}/usr/bin/loch
  install -m644 -D therion.ini ${pkgdir}/etc/therion/therion.ini
  install -m644 -D xtherion/xtherion.ini ${pkgdir}/etc/therion/xtherion.ini

  # additional install rules from makebinary.pl
  install -m644 -D man/therion.1 ${pkgdir}/usr/share/man/man1/therion.1
  install -m644 -D man/xtherion.1 ${pkgdir}/usr/share/man/man1/xtherion.1

  mkdir -p ${pkgdir}/usr/share/doc/therion
  cp -a \
    CHANGES COPYING README SVG.problems SYMBOLS.txt \
    TODO.M TODO.MS TODO.S TODO.SM thbook/thbook.pdf samples \
    ${pkgdir}/usr/share/doc/therion
}

# vim:set ts=2 sw=2 et:
