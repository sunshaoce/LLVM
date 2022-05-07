# LLVM 简介及配置

## 简介
LLVM是一个编译程序库，包含了基于llvm的项目，例如：clang（音为/klæŋ/）、libc等项目。现在clang发展迅速，并在MacOS等平台上取代gcc成为了默认的C语言编译器。

## 下载

采用源码编译的方式。

```shell
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build
cd build
cmake -GNinja ../llvm
ninja
```
### git clone

git相关资料参考[Git 入门](./git_intro.md)。

### cd、mkdir

git相关资料参考[Linux 入门](./linux_intro.md)。

### cmake

cmake是一个跨平台的代码构建系统。其在构建LLVM的时候，可以使用多个以DCMAKE开头的参数：

- `-DCMAKE_C_COMPILER=`：设置编译此项目所用的C语言编译器。例如`-DCMAKE_C_COMPILER=clang`，或者指明路径`-DCMAKE_C_COMPILER=/usr/bin/clang`。

- `-DCMAKE_CXX_COMPILER=`：设置编译此项目所用的C++语言编译器。

- `-DCMAKE_USE_LINKER=`：设置编译此项目所用的链接器。

同时，LLVM项目中，也包含有大量的变量：

- `-DLLVM_TARGETS_TO_BUILD=`：LLVM默认构建所有目标平台（包括X86、AArch64、RISC-V等），如果我们只启用X86和RISC-V平台，则可设置为`-DLLVM_TARGETS_TO_BUILD="X86;RISCV"`。

- `-DLLVM_ENABLE_PROJECTS=`

- `-DLLVM_EXPENSIVE_CHECKS=`

- `-G Ninja`

### ninja
