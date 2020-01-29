# Maintainer: Shun Terabayashi <shunonymous@gmail.com>
# Contributor: xgdgsc <xgdgsc @t gmail dot com>

pkgname=android-rebuilds-sdk-build-tools-bin
_ver=29.0.2
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

source=("https://android-rebuilds.beuc.net/dl/repository/sdk-repo-linux-build-tools-eng.10.0.0_r14.zip")
sha256sums=('e9e16315087925f35ea25cb17f1892a29772cfc00db7ad7542703da427f9dfac')
_android=android-10
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
