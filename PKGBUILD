pkgname=ropieee-4.9.52-taudac
pkgver=2.2.2
pkgrel=1
pkgdesc="Kernel modules for the TauDAC-DM101 Raspberry Pi sound card."
arch=('armv7h')
depends=('linux-firmware>=20171009' 'linux-raspberrypi-dsd>=4.9.52')
makedepends=('git' 'make' 'gcc' 'bc')
url="http://taudac.com/"
source=("git+https://github.com/taudac/taudac-driver-dkms.git#tag=taudac-$pkgver")
md5sums=('SKIP')

install=taudac.install

pkgver() {
	# Sanity check, this should not change $pkgver
	git -C $srcdir/taudac-driver-dkms describe --tags | sed 's/taudac-//;s/\([^-]*-g\)/r\1/;s/-/_/g'
}

build() {
	make -C $srcdir/taudac-driver-dkms/src
}

package() {
	make -C $srcdir/taudac-driver-dkms/src PACKAGEDIR="$pkgdir/usr" package
}

