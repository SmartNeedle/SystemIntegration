3D Slicer Setup - Ubuntu 22.04
===================

3D Slicer
--------------

To use SlicerROS2, we have to use a compiled version of 3D Slicer
* Download 3D Slicer source code (v. 5.7.0): https://github.com/Slicer/Slicer.git
* Compile 3D Slicer ([build instructions for Ubuntu 22.04](https://slicer.readthedocs.io/en/latest/developer_guide/build_instructions/linux.html#ubuntu-22-04-jammy-jellyfish)).
  **Before you start compiling Slicer**, make sure we use the system/native OpenSSL libraries otherwise you’ll get some errors when compiling the Slicer ROS 2 module.
  You will need to do the following after you ran CMake for the first time:
  * In the Slicer build directory, set Slicer_USE_SYSTEM_OpenSLL to ON using
    ```cmake . -DSlicer_USE_SYSTEM_OpenSSL=ON -DCMAKE_BUILD_TYPE=Release``` or ```ccmake.``` with Local Open SSL option
* Install ROS2 Humble: [Instructions](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)

SlicerROS2
--------------------

* Download SlicerRO2 source: https://github.com/rosmed/slicer_ros2_module
* Compile SlicerROS2 module: [Instructions](https://slicer-ros2.readthedocs.io/en/latest/pages/getting-started.html#compilation)

Other required Slicer Modules
--------------------

* SlicerOpenIGTLink: https://github.com/openigtlink/SlicerOpenIGTLink.git
* SlicerDevelopmentToolbox: https://github.com/QIICR/SlicerDevelopmentToolbox.git
* ZFrameRegistration (modified to choose different ZFrame model): https://github.com/maribernardes/ZFrameRegistration-3DSlicer.git
* CurveMaker (modified to remove deprecated method): https://github.com/maribernardes/CurveMaker-3DSlicer
* SmartNeedle: https://github.com/maribernardes/SmartNeedle-3DSlicer.git
