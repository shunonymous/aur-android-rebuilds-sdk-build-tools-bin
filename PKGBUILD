# Maintainer: Shun Terabayashi <shunonymous@gmail.com>
# Contributor: xgdgsc <xgdgsc @t gmail dot com>

pkgname=android-rebuilds-sdk-build-tools-bin
_ver=30.0.3
pkgver=r$_ver
pkgrel=1
pkgdesc='Build-Tools for Android SDK provided by Android Rebuilds (aapt, aidl, dexdump, dx, llvm-rs-cc)'
arch=('i686' 'x86_64')
url="https://android-rebuilds.beuc.net/"
license=('custom')
depends=('gcc-libs' 'zlib')
optdepends=('lib32-gcc-libs' 'lib32-zlib')
provides=('android-sdk-build-tools')
_sdk=android-sdk

source=("https://android-rebuilds.beuc.net/dl/repository/sdk-repo-linux-build-tools-eng.11.0.0_r27.zip")
sha256sums=('53973f73e9a60829c4f920acbed5fe5e784b5efc0972f09938da185c384e3470')
_android=android-11
options=('!strip')

package() {

  cd "$pkgdir"
  install -Dm644 "${srcdir}/$_android/NOTICE.txt" usr/share/licenses/$pkgname/NOTICE.txt
  # mkdir -p opt etc/profile.d
  # echo 'export PATH=$PATH:/opt/android-sdk/build-tools/'"$_ver/" > etc/profile.d/${pkgname}.sh
  # echo 'setenv PATH ${PATH}:/opt/android-sdk/build-tools/'"$_ver/" > etc/profile.d/${pkgname}.csh
  # chmod 755 etc/profile.d/${pkgname}.{csh,sh}
  ver=$(cat "${srcdir}/$_android/source.properties" |grep ^Pkg.Revision=|sed 's/Pkg.Revision=\([0-9.]*\).*/\1/')
  mkdir -p opt/$_sdk/build-tools/$ver
  cp -r "$srcdir/$_android/"* "$pkgdir/opt/$_sdk/build-tools/$ver"
  chmod +Xr -R "$pkgdir/opt/$_sdk/build-tools/$ver"
}
