# Maintainer: David Roheim <david dot roheim at gmail dot com>
# Constributor: Chris Heien <chris.h.heien@gmail.com>
# Constributor: Jonny Gerold <jonny@fsk141.com>

pkgname=s3fs
_filename=${pkgname}-fuse
pkgver=1.78
pkgrel=1
pkgdesc="FUSE-based file system backed by Amazon S3"
arch=('i686' 'x86_64')
url="https://github.com/s3fs-fuse/s3fs-fuse/wiki"
license=('GPL2')
depends=('fuse>=2.8.4' 'glib2' 'libxml++' 'mime-types')
source=("${_filename}-${pkgver}.tar.gz::https://github.com/s3fs-fuse/s3fs-fuse/archive/v${pkgver}.tar.gz")
sha256sums=('36c0b00a294d9676c462985c0c3f1362540e8ebc61c15bacb45e28a2f00297f5')

build() {
        cd ${srcdir}/${_filename}-${pkgver}
	./autogen.sh
        ./configure --prefix=/usr || return 1
        make || return 1
}

package() {
	cd ${srcdir}/${_filename}-$pkgver
	install -Dm644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
        make DESTDIR="${pkgdir}/" install	
}
