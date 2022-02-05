# 1. Environment Setup

## 1.0 catkin not found
Maybe you didn't install "catkin ROS build system". You can install it using the following command for ROS Melodic:\
`sudo apt-get install ros-melodic-catkin python-catkin-tool`

## 1.1 glog not found
Install the glog lib:\
`sudo apt install libgoogle-glog-dev`

Then add in src/[package_name]/CMAKELIST.txt:\
`find_package(glog)`

## 1.2 geographiclic
- `sudo apt-get install libgeographic-dev`
- CMAKE error:
```bash
CMake Error at CMakeLists.txt:3 (find_package):
  By not providing "FindGeographicLib.cmake" in CMAKE_MODULE_PATH this
  project has asked CMake to find a package configuration file provided by
  "GeographicLib", but CMake did not find one.
```
- To solve this error, refer to this [link](https://stackoverflow.com/questions/48169653/finding-geographiclib-in-cmake-on-debian).

```bash
According to this Bug Report,

The geographiclib-dev installer puts the FindGeographicLib.cmake file in: /usr/share/cmake/geographiclib/FindGeographicLib.cmake

The correct location is: /usr/share/cmake-3.5/Modules

Indeed it depends by the version of cmake currently installed. In Ubuntu 18.04, it is 3-10. So you can fix the issue this way:

sudo ln -s /usr/share/cmake/geographiclib/FindGeographicLib.cmake /usr/share/cmake-3.10/Modules/
```

