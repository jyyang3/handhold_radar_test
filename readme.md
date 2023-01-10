This is a test ros package for mmWave radar SLAM with only pointcloud data provided by mmWave radar. 

Derived from: https://github.com/nhma20/iwr6843aop_pub

Prerequisites:
1.ROS2(Ubuntu 20.04 &foxy)
2.Python3
3.IWR6843 mmWave radar device flashed with out-of-box firmware
4.ros2 packages:ros-foxy-cartographer, ros-foxy-cartographer-ros

To run the mmWave radar SLAM 
1."ros2 run iwr6843_pub pcl_pub"
2."ros2 launch radar_cartographer cartographer.launch.py"

the published frame for mmWave radar is called "iwr6843_frame"


Given enough initialization time, it's possible to perform some localization purely based on data from mmWave sensor. But the performance depends heavily on the environment setup. In real implementation, It's better to use odometry data to provide supplementary information.

give fixed port name to serial devices:
1.udevadm info --attribute-walk --name=/dev/ttyUSB0
2.check third "look at" ,record KERNELS == ???? ,e.g. KERNELS=="2-3:1.0"
3.sudo gedit /etc/udev/rules.d/usb.rules
4.enter "KERNELS=="2-3:1.0", MODE:="0777", GROUP:="dialout", SYMLINK+="radar/drone/etc.""
