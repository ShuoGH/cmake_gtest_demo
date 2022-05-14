## 该工程下的GTest测试

根据该工程下gtest的部署，进行LLT测试的话，主要由以下四个步骤组成。

1. 切换到build目录下

`cd build`

2. 创建cmake系统

`cmake ../ .`

3. 编译

`cmake --build .`

4. 执行llt测试用例

`./tst/ExampleProject_tst`

这里的关键在于CMakelist.txt文件的内容及组织。该工程下无法通过ctest直接调用测试，这个后续再看如何改进，anyway，当前能够已经能够通过嵌入googletest成功调用gtest了。



##更简单的GTEST Demo

其实在这个目录的父目录下，以及同级目录下，有更简单的gtest的调用，但是那个因为需要构建cmake工程的时候fetch github下的googletest的repo，所以才又有了这个工程的尝试。

通过fetch的方式构建gtest测试的，可以查看`../CMakeLists.txt`以及`../sample1/CMakeLists.txt`的内容组织。

调用方式：

`cmake ./ -B build `

`cmake --build ./build/`



## Reference:

1. https://raymii.org/s/tutorials/Cpp_project_setup_with_cmake_and_unit_tests.html  PDF文件形式的也放到这个文件夹的根目录下了。