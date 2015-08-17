# Maintainer: Lucas Katayama <lucaskatayma[at]gmail[dot]com>
pkgname=robomongo-git
pkgver=0.8.5
pkgrel=1
_pkg=robomongo
_pkgtype=Release
pkgdesc="Shell-centric cross-platform MongoDB management tool"
url="http://robomongo.org"
arch=('x86_64' 'i686')
license=('GPLv3')
conflicts=("robomongo")
depends=("qt5-base" "scons" "pcre") 

if [[ "$CARCH" == "x86_64" ]]; then
  _iarch='64'
elif [[ "$CARCH" == "i686" ]]; then
  _iarch='32'
fi

optdepends=()
makedepends=()
conflicts=()
replaces=()
backup=()
install=''
source=("https://github.com/paralect/robomongo/archive/v${pkgver}.tar.gz")
md5sums=('e203d548390282e00e2c27c5bd42b5ea')

build() {
  cd ${srcdir}/${_pkg}-${pkgver}
  mkdir -p target
  cd target
  cmake .. -DCMAKE_BUILD_TYPE=${_pkgtype} -DOS_ARC=${_iarch}
  make
  make install
  
}

package() {
  _destdir=${pkgdir}/opt/${pkgname}
  _installdir=${srcdir}/${_pkg}-${pkgver}/target/install
  mkdir -p ${_destdir} ${pkgdir}/usr/bin
  echo ${_installdir}
  cp -rdp ${_installdir}/* ${_destdir}/

  ln -s  /opt/${pkgname}/bin/robomongo ${pkgdir}/usr/bin/robomongo

  install -Dm0644 "${_destdir}/share/applications/robomongo.desktop" "${pkgdir}/usr/share/applications/robomongo.desktop"
  install -Dm0644 "${_destdir}/share/icons/robomongo.png" "${pkgdir}/usr/share/pixmaps/robomongo.png"
  install -Dm0644 "${_destdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"

}

# vim:set ts=2 sw=2 et:
