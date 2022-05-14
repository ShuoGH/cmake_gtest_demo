#基于gtest和cmake的demo

gtest的代码主要是基于googletest的repo中的sample进行的测试。

结合cmake进行的工程小实践。

## 1. gtest_demo

使用的是googletest中推荐的方式，根据其教程来的简单的方式进行的。

通过CMakeLists.txt中的FetchContent来获取googletest中的内容，简单方便。

`cd gtest_demo`

`cmake ./-B build `

`cmake --build ./build`

`cd build && ctest`

可以直接通过ctest来调用相关的测试用例。

**Reference**: [Quickstart: Building with CMake](https://google.github.io/googletest/quickstart-cmake.html)

## 2. gtest_sample2

使用的是工程化的方式，没有采取FetchContent的方式，而是通过将googletest的代码嵌入代码目录中的方式来进行的。主要参考的是这篇[博客](https://raymii.org/s/tutorials/Cpp_project_setup_with_cmake_and_unit_tests.html )。

对应目录下也有相应的readme.md文档。

`cd gtest_sample2/build`

`cmake ../ .`

`cmake --build .`

`./tst/ExampleProject_tst`

这个会生成对应的用例的可执行文件，通过调用这个可执行文件来执行测试。

**Reference**：[C++ project setup with CMake & unit tests (google test)](https://raymii.org/s/tutorials/Cpp_project_setup_with_cmake_and_unit_tests.html)

## 3. gtest_sample2_dylib

与上面gtest_sample2不一样的是，这个用于测试的对象不是源代码，而是已经编译生成的so文件。CMakeLists.txt文件有对应的修改。

`cd gtest_sample2_dylib/build`

`cmake ../ .`

`cmake --build .`

在执行用例的二进制文件前，需要将对应的so文件复制到系统环境的路径下，或者对应二进制所在目录下。

`cd tst && ./ExampleProject_tst `



##Reference：

1. 很有用的blog，工程框架主要是借鉴这篇blog中的内容 https://raymii.org/s/tutorials/Cpp_project_setup_with_cmake_and_unit_tests.html 
2. googletest的代码仓 https://github.com/google/googletest 
3. cmake官方文档 https://cmake.org/cmake/help/latest/index.html 

以及部分stackoverflow相关的问答





