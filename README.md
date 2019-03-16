# HI!
三个源文件
```
/* solution.h */
class Solution {
public:
    void Say();
 };
 ```
 ```
 /* solution.cpp */
#include <iostream>
#include "solution.h"
void Solution::Say(){
   std::cout << "HI!" << std::endl;
}
```
```
/* hw2.cpp */
#include "solution.h"
int main () {
    Solution sln;
    sln.Say();
    return 0;
}
```

## 1.g++编译

在项目的根目录下打开终端运行

```
[xxx@xxx ~]$ g++ -c hw2.cpp
[xxx@xxx ~]$ g++ -c solution.cpp
```
生成 hw2.o solution.o 

```
[xxx@xxx ~]$ g++ -o build hw2.o solution.o
```

生成build文件

```
[xxx@xxx ~]$ ./build 
HI!
```
## 2.make编译
在项目的根目录下创建一个makefile文件
``` 
build : hw2.o solution.o
    g++ -o build hw2.o solution.o 
hw2.o : hw2.cpp solution.h
    g++ -g -c hw2.cpp
solution.o : solution.h solution.cpp
    g++ -g -c solution.cpp
clean :
    rm hw2.o solution.o build
```
在项目的根目录下打开终端执行
```
[xxx@xxx ~]$ make
g++ -g -c hw2.cpp
g++ -g -c solution.cpp
g++ -o build hw2.o solution.o 
[xxx@xxx ~]$ ./build 
HI!
```
## 3.cmake编译
在项目的根目录下创建文件CMakeLists.txt

```
cmake_minimum_required(VERSION 2.8)
 
 project(demo2)
 
 add_executable(build hw2.cpp solution.cpp)
 ```
 在项目的根目录下打开终端运行
 ```
 [xxx@xxx ~]$ cmake .
 
 [xxx@xxx ~]$ make
 
 [xxx@xxx ~]$ ./build
 HI!
 ```

