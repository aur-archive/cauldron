# Maintainer: Vinzenz Vietzke <vinz at vinzv dot de>
pkgname=cauldron
pkgver=0.18.0
pkgrel=1
pkgdesc="A cross-platform desktop client for App.net."
url="https://cauldron-app.herokuapp.com/"
license=('custom')
depends=('gtk2' 'alsa-lib' 'gconf' 'nss')
options=(!strip)
arch=('x86_64' 'i686')
conflicts=('libudev.so.0')

source=('https://files.app.net/zrxg_egM' 'cauldron.png' 'cauldron.desktop' 'run-cauldron.sh')
md5sums=('a4f2745b6ad45e40fd7ebae6a9c14da1' '0f0142efeaf7dc58753e0eb4821a73b4' '59d4fb3b411ed905b3282837d857dfc0' 'f0ad02d5c2f1cfdb73c38997a5102056')

if [[ "$CARCH" == "i686" ]]; then
	source[1]=https://files.app.net/zs5846Zz
	md5sums[1]='f898dd466868c52766d40bd8d70feea4'
fi

package() {
	install -Dm 755 run-cauldron.sh "$pkgdir/usr/bin/cauldron"

	_destdir="$pkgdir/opt/cauldron"

	install -dm755 $_destdir
	mv "$srcdir/cauldron/cauldron" $_destdir
	mv "$srcdir/cauldron/nw.pak" $_destdir
	mv "$srcdir/cauldron/libffmpegsumo.so" $_destdir

	mkdir -p "${pkgdir}"/usr/share/{applications,pixmaps,licenses/cauldron}
	install -m644 "${srcdir}"/cauldron/LICENSE.txt "${pkgdir}"/usr/share/licenses/cauldron/
	install -m644 "${startdir}"/cauldron.desktop "${pkgdir}"/usr/share/applications/
	install -m644 "${startdir}"/cauldron.png "${pkgdir}"/usr/share/pixmaps/cauldron.png

	mkdir -p "$pkgdir/usr/lib"
	ln -s /usr/lib/libudev.so "$pkgdir/usr/lib/libudev.so.0"
}


