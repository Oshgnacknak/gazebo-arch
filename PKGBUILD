# Maintainer: Troy Patrick <patrictroy at gmail dot com>
# Maintainer: racko <tim dot rakowski at gmail dot com>
# Contributor: marauder <abhinav dot kssk at gmail dot com>
# Contributor: Benjamin Chretien <chretien at lirmm dot fr>
# Contributor: Anton Bazhenov <anton.bazhenov at gmail>
# Contributor: Vladimir Ermakov <vooon341@gmail.com>

pkgname=gazebo
pkgver=9.6.0
pkgrel=2
pkgdesc="A multi-robot simulator for outdoor environments"
arch=('i686' 'x86_64')
url="http://gazebosim.org/"
license=('Apache')
# See: http://www.gazebosim.org/tutorials?tut=install_from_source&cat=install
depends=('boost>=1.40.0' 'curl>=4.0' 'freeglut' 'freeimage>=3.0'
         'intel-tbb>=3.0' 'libccd>=1.4' 'libltdl>=2.4.2' 'libtar>=1.2' 'libxml2>=2.7.7'
         'ogre-1.9' 'protobuf>=2.3.0' 'sdformat>=6.0.0' 'ignition-math>=4' 'ignition-transport>=4'
         'ignition-common' 'ignition-fuel_tools' 'ignition-msgs' 'tinyxml2' 'qwt')
optdepends=('bullet: Bullet support'
            'cegui: Design custom graphical interfaces'
            'ffmpeg: Playback movies on textured surfaces'
            'gdal: Digital elevation terrains support'
            'libdart: DART support'
            'libspnav: space navigator joystick support'
            'libusb: USB peripherals support'
            'ruby-ronn: Generate manpages'
            'simbody: Simbody support'
            'urdfdom: Load URDF files')
makedepends=('cmake' 'doxygen' 'ignition-cmake')
install="${pkgname}.install"
source=("https://bitbucket.org/osrf/gazebo/get/gazebo9_${pkgver}.tar.bz2")
sha256sums=('ebfc99ae8256492ba1ab23b77a59e2149da8a968f9b1c2132a42cd9c8225db57')

prepare() {
    cd "${srcdir}/osrf-${pkgname}-04a40b564570"
}

build() {
  cd "${srcdir}/osrf-${pkgname}-04a40b564570"

  mkdir -p build && cd build

  export PKG_CONFIG_PATH="/opt/OGRE-1.9/lib/pkgconfig"

  # Note: we skip unit tests (else set to TRUE)
  cmake .. -DCMAKE_BUILD_TYPE="Release" \
           -DCMAKE_INSTALL_PREFIX="/usr" \
           -DCMAKE_INSTALL_LIBDIR="lib"
  make
}

package() {
  cd "${srcdir}/osrf-${pkgname}-04a40b564570/build"
  make DESTDIR="${pkgdir}" install
}
