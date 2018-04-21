# Script generated with Bloom
pkgdesc="ROS - Capture is a set of tools to capture objects in 3D and perform odometry"
url='http://wg-perception.github.io/capture'

pkgname='ros-kinetic-object-recognition-capture'
pkgver='0.3.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('boost'
'ros-kinetic-catkin'
'ros-kinetic-ecto'
'ros-kinetic-object-recognition-core'
)

depends=('boost'
'ros-kinetic-ecto'
'ros-kinetic-ecto-image-pipeline'
'ros-kinetic-ecto-opencv'
'ros-kinetic-ecto-openni'
'ros-kinetic-ecto-ros'
'ros-kinetic-object-recognition-core'
)

conflicts=()
replaces=()

_dir=object_recognition_capture
source=()
md5sums=()

prepare() {
    cp -R $startdir/object_recognition_capture $srcdir/object_recognition_capture
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

