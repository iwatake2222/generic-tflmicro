# generic-tflmicro
- This repository provides:
	- cmake project to generate TensorFlow Lite for Microcontrollers ( TFLM ) as a library
		- You can easily use TFLM in your project by adding this repository as git-submodule
	- sample project (hello world project) to use the TFLM library

- The TFLM library in this repo doesn't have platform-specific hardware optimizations. So the library should run on any platform
	- I made this repository mainly for development on PC (Windows and Linux on x64)
	- When you use a specific hardware like Arduino, it' better to create a new library for the device to get better performance

## How to build
### PC Linux (x64)
```sh
mkdir -p build && cd build/
cmake ..
make -j4
./examples/hello_world/hello_world 
```
### Windows (Visual Studio 2019) (x64)
- Use cmake-gui

## How to use in your project
Refer to [examples/hello_world/CMakeLists.txt](examples/hello_world/CMakeLists.txt)

## How this repository was generated
- Clone code and generate all projects
	- It's actually no need to generate all projects, but just generating hello_world project didn't work to me
```sh
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
# git checkout 1e8f4666f2fbc1bdd4ce2797b218de0453cffc63

make -f tensorflow/lite/micro/tools/make/Makefile generate_projects
# make -f tensorflow/lite/micro/tools/make/Makefile generate_hello_world_make_project

ls tensorflow/lite/micro/tools/make/gen/linux_x86_64_default/prj/hello_world/tensorflow_lite.zip
```

- Add CMakeLists.txt files
- Do some modifications (see commit log to find diff)

