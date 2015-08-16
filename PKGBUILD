# Maintainer: (epsilom) Xavier Corredor <xavier.corredor.llano (a) gmail.com>
pkgname=jaziku-dev
_pkgname=jaziku
pkgver=0.5.2
pkgrel=1
pkgdesc="Jaziku is statistical inference software for the teleconnections analysis"
url="http://hg.ideam.gov.co:8000/meteorologia/jaziku/summary"
arch=('i686' 'x86_64')
license=('GPLv3')
depends=('python2' 'python2-distribute' 'python2-scipy' 'python2-dateutil' 'python2-matplotlib' 'python2-numpy' 'python-imaging' 'python2-clint' 'imagemagick' 'hpgl' 'ncl')
#makedepends=('python2-distribute')
source=("http://dl.dropbox.com/u/3383807/jaziku-$pkgver.tar.gz")
md5sums=('e58ce34ba23d069430ef3d6283890a60')

build() {
	cd ${srcdir}/$_pkgname-$pkgver
	cd bin
	mv jaziku jaziku-dev
	sed -i 's/from jaziku/from jaziku_dev/g' jaziku-dev
	cd ..
	find . -iname '*.py' | xargs sed -i 's/from jaziku./from jaziku_dev./g'
    mv jaziku jaziku_dev
	sed -i 's|bin/jaziku|bin/jaziku-dev|g' setup.py
	sed -i 's|jaziku/|jaziku_dev/|g' MANIFEST.in
	python2 ./setup.py build || return 1
}

package(){
	cd ${srcdir}/$_pkgname-$pkgver
	python2 ./setup.py install --root=$pkgdir || return 1
}
