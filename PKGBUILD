pkgname=rune-4.9.73-taudac
pkgver=2.2.2
pkgrel=2
pkgdesc="Kernel modules for the TauDAC-DM101 Raspberry Pi sound card."
arch=('armv7h')
depends=('linux-firmware>=20160113' 'linux-raspberrypi>=4.9.73')
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
	sed -e "s/KERNELVER=.*/KERNELVER=$(uname -r)/g" -i $startdir/taudac.install
	make -C $srcdir/taudac-driver-dkms/src PACKAGEDIR="$pkgdir/usr" package
}

