pkgname=rune-4.19.80-taudac
pkgver=2.4.0
pkgrel=1
pkgdesc="Kernel modules for the TauDAC-DM101 Raspberry Pi sound card."
arch=('armv7h')
depends=('linux-firmware>=20180314' 'linux-raspberrypi>=4.19.80')
makedepends=('git' 'make' 'gcc' 'glibc' 'bc')
url="http://taudac.com/"
source=("git+https://github.com/taudac/taudac-driver-dkms.git#tag=taudac-$pkgver")
md5sums=('SKIP')

install=taudac.install

pkgver() {
	# Sanity check, this should not change $pkgver
	git -C $srcdir/taudac-driver-dkms describe --tags | sed 's/taudac-//;s/\([^-]*-g\)/r\1/;s/-/_/g'
}

build() {
	# We need to patch a kernel header for experimental si5351 sync_mode support
	# patch --directory=/usr/lib/modules/$(uname -r)/build/ -p0 < si5351.h_sync_mode.patch
	make -C $srcdir/taudac-driver-dkms/src
}

package() {
	sed -e "s/KERNELVER=.*/KERNELVER=$(uname -r)/g" -i $startdir/taudac.install
	make -C $srcdir/taudac-driver-dkms/src \
		INSTALL_TO_ORIGDIR=1 \
		RELEASEDIR="$pkgdir/usr/lib/modules/$(uname -r)" \
		release
}

