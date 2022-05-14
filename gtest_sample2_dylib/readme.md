## Gtest 测试SO文件



这里将gtest结合起来用于测试so文件。

### 1. 将src编译为对应的so

对应的命令行：

`g++ sample2.cpp -std=c++11 -fPIC -shared -o libsample2.so`

这里是编译cpp文件，所以用的是g++，并且有C++11的特性，要对应-std=c++11.

### 2. 修改cmake用于测试so文件

主要修改了用于tst测试用的cmakelists.txt文件。关于链接第三方so文件，推荐使用

`add_library( libsample SHARED IMPORTED GLOBAL)`

`set_target_properties( libsample PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/include/libsample2.so )`

###3. 构架新的cmake并进行编译

`cd build`

`cmake ../ .`

`cmake --build .`

注意这里要是调用test的话，需要将libsample2.so放置在build/tst/目录下（或者放在`$PATH`对应的目录下）。因为这个命令调用gtest可执行文件的时候会去链这个so库文件。

`cd tst`

`./ExampleProject_tst`

![Snipaste_2022-05-15_00-57-58](/Users/shuo/Desktop/mycode/cmake_gtest_demo/gtest_sample2_dylib/others/Snipaste_2022-05-15_00-57-58.png)

Reference:

1. Make to link external library https://stackoverflow.com/questions/8774593/cmake-link-to-external-library 



