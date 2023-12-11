# Maintainer: Timothy Gelter <timothy dot gelter plus aur at gmail dot com>
pkgname=globalprotect-bin
pkgver=6.1.2.0
pkgrel=82
pkgdesc="GlobalProtect VPN client Agent"
arch=('x86_64')
url="https://docs.paloaltonetworks.com/globalprotect/5-2/globalprotect-app-user-guide/globalprotect-app-for-linux/download-and-install-the-globalprotect-app-for-linux"
license=('custom')
groups=()
depends=('qt5-webkit' 'wmctrl')
options=('!strip')
install=globalprotect.install
source=("local://GlobalProtect_UI_tar-$pkgver-$pkgrel.tgz")
sha256sums=('7f38958a1f1287cc6d3182cfb4d9c4137a9ad5e9827f7d6a013989fa679b364d')

package(){
	# Adapted for Arch Linux from package tarball's install.sh
	GPDIR="$pkgdir/opt/paloaltonetworks/globalprotect"
	mkdir -m 755 -p $GPDIR
	# skipping install logging for packaging purposes
	cp -f globalprotect PanGPA PanGPS PanGpHip PanGpHipMp $GPDIR/
	cp -df *.so* $GPDIR/
	# TODO: Test/fixup gpshow.sh gp_support.sh, as needed
	cp -f license.cfg gpd gpd.service gpa.service PanMSInit.sh pre_exec_gps.sh gpshow.sh gp_support.sh globalprotect.1.gz \
		PanGPUI.desktop PanGPUI globalprotect.png gp.desktop globalprotect.desktop $GPDIR/
	# TODO: post-install script to run update-desktop-database so the desktop files are known w/out reboot?
	install -Dm644 $GPDIR/PanGPUI.desktop "$pkgdir/usr/share/applications/PanGPUI.desktop"
	install -Dm755 $GPDIR/PanGPUI "$pkgdir/PanGPUI"
	install -Dm644 $GPDIR/globalprotect.png "$pkgdir/usr/share/icons/hicolor/48x48/apps/globalprotect.png"
	install -Dm644 $GPDIR/gp.desktop "$pkgdir/usr/share/applications/gp.desktop"
	install -Dm644 $GPDIR/globalprotect.desktop "$pkgdir/usr/share/applications/globalprotect.desktop"
	install -Dm644 $GPDIR/globalprotect.1.gz "$pkgdir/usr/share/man/man1/globalprotect.1.gz"
	install -Dm755 $GPDIR/globalprotect "$pkgdir/usr/bin/globalprotect"
	install -Dm644 $GPDIR/gpd.service "$pkgdir/usr/lib/systemd/system/gpd.service"
	install -Dm644 $GPDIR/gpa.service "$pkgdir/usr/lib/systemd/user/gpa.service"
	install -Dm644 $GPDIR/PanMSInit.sh "$pkgdir/etc/profile.d/PanMSInit.sh"
}
