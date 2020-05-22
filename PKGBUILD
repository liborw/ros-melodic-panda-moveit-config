pkgname="ros-melodic-panda-moveit-config"
pkgver="0.7.3"
pkgrel=1
pkgdesc="Franka Emika Panda MoveIt! Config Package"
arch=(x86_64)
url="http://wiki.ros.org/panda_moveit_config"
license=('Apache')

ros_makedepends=(
    'ros-melodic-catkin'
)

makedepends=(
    'cmake'
    'ros-build-tools'
    ${ros_makedepends[@]}
)

ros_depends=()

depends=(
    ${ros_depends[@]}
)

provides=($pkgname)
conflicts=($pkgname)
_dir="panda_moveit_config-$pkgver"
source=("ros-melodic-panda-moveit-config-$pkgver.tar.gz::https://github.com/ros-planning/panda_moveit_config/archive/$pkgver.tar.gz")
sha256sums=(740cf19109e6fb74de9462ff264c4da4f88ac2f0e4d34b76e6d8db30b7a38e3a)


build() {
	# Use ROS environment variables
  	source /usr/share/ros-build-tools/clear-ros-env.sh
  	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create build directory
  	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  	cd ${srcdir}/build

	# Build project
	cmake ${srcdir}/${_dir} \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DCATKIN_BUILD_BINARY_PACKAGE=ON \
	      -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
	      -DPYTHON_EXECUTABLE=/usr/bin/python3 \
	      -DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
