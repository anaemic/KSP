# Maintainer: J0k3r <moebius282 e4at gmail D0_T com>

pkgname=kerbalspaceprogram
pkgver=1.2.2
pkgrel=1
pkgdesc="A multi-genre game where the players create their own space program."
url="https://kerbalspaceprogram.com/"
license=('unknown')
arch=('i686' 'x86_64')
groups=("games")
depends=('gcc-libs' 'libgl' 'glu' 'libxcursor')
makedepends=('unzip')
# install="$pkgname.install"		
_archivename="ksp-linux-$pkgver"
source=("$_archivename.zip" "$pkgname.desktop")
sha256sums=('c0e0c217cd725625d00d51eab7e49d2d34a7f791e00caf40b212f4252a2eb556' 
'e6591e5ddf03308515c493f267ee7464a7897d8db07bc2353abde661032a1e64')

PKGEXT=".pkg.tar"

DLAGENTS+=('file::/usr/bin/echo "Could not find file \"%u\" "')


package()
{
	install -d "$pkgdir/opt/"

# took me ~2h to know what has to have which permissions..
	cp -r "$srcdir/KSP_linux/" "$pkgdir/opt/$pkgname"

	cd "$pkgdir/opt/$pkgname"

	install -d -m777 "Screenshots/" "Plugins/" "PluginData/"
	chmod -R 0777 "saves/"
	
	touch "settings.cfg" "KSP.log"
	chmod o+w "settings.cfg" "KSP.log"

# I don't know if i should cry or laugh..
# For the ASSETS! directory; needs executable and write on all files!?
# Fun Fact: It doesn't even write to it.
	chmod -R 0777 "GameData/"

# TODO: add more unneeded files and remove the bundled mono
	for i in "${_purgefiles[@]}"; do
		echo "Removing unneeded file: $i"; rm "$i"
	done

	install -d "$pkgdir/usr/bin/"

	if [[ "$CARCH" == "x86_64" ]]; then
		ln -s "/opt/$pkgname/KSP.x86_64" "$pkgdir/usr/bin/$pkgname"
	else
		ln -s "/opt/$pkgname/KSP.x86" "$pkgdir/usr/bin/$pkgname"
	fi


	install -D -m644 "$srcdir/$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
	# install -D -m644 "$pkgdir/opt/$pkgname/$pkgname.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
}
