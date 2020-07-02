# cpprestsdk 使用例子

## 内容列表
- [cpprestsdk 使用例子](#cpprestsdk-使用例子)
  - [内容列表](#内容列表)
  - [静态库使用](#静态库使用)

## 静态库使用
1. 获取cpprestsdk 静态库 :  vcpkg install cpprestsdk:x86-windows-static
2. 编译本工程
   1. mkdir build && cd build
   2. cmake ../ -A win32 -DVCPKG_ROOT_DIR=${your_vcpkg_root_dir}
   3. cmake --build .