pkgname=ropieee-4.9.43-taudac
pkgver=2.2.2
pkgrel=1
pkgdesc="Kernel modules for the TauDAC-DM101 Raspberry Pi sound card."
arch=('armv7h')
url="http://taudac.com/"
depends=('linux-raspberrypi-dsd>=4.9.43-2')
#source=("https://github.com/taudac/taudac-driver-dkms/archive/master.tar.gz")

install=taudac.install

pkgver() {
	git -C ../../taudac-driver-dkms describe --tags | sed 's/taudac-//;s/\([^-]*-g\)/r\1/;s/-/_/g'
}

build() {
	make -C ../../taudac-driver-dkms/src
}

package() {
	make -C ../../taudac-driver-dkms/src PACKAGEDIR="$pkgdir/usr" package
}

