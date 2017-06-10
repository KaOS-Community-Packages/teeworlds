pkgname=teeworlds
pkgver=0.6.4
pkgrel=1
pkgdesc='Fast-paced multiplayer 2D shooter game'
arch=('x86_64')
url='https://www.teeworlds.com'
license=('custom')
depends=('alsa-lib' 'glu' 'sdl' 'freetype2')
makedepends=('bam' 'mesa')
source=("https://downloads.teeworlds.com/teeworlds-${pkgver}-src.tar.gz"
        "teeworlds.desktop"
        "teeworlds.png"
)
md5sums=('9733800c12462ac4d5a5a4f6ea750af0'
         '6d72b8c56db2cfc82305b3fa8ed36c18'
         'f0e2b30497773bd05a1d7a506bcdf27e'
)

build() {
  cd "$pkgname-$pkgver-src"
  bam server_release client_release
}

package() {
  cd "$pkgname-$pkgver-src"

  mkdir -p ${pkgdir}/usr/share/${pkgname}/data
  cp -r data/* ${pkgdir}/usr/share/${pkgname}/data

  install -Dm755 ${pkgname} ${pkgdir}/usr/bin/${pkgname}
  install -Dm755 ${pkgname}_srv ${pkgdir}/usr/bin/${pkgname}_srv

  install -Dm644 ${srcdir}/${pkgname}.desktop ${pkgdir}/usr/share/applications/${pkgname}.desktop
  install -Dm644 ${srcdir}/${pkgname}.png ${pkgdir}/usr/share/pixmaps/${pkgname}.png

  install -Dm644 license.txt ${pkgdir}/usr/share/licenses/${pkgname}/license.txt
}
