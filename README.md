# LLVM binaries
Prebuilt versions of LLVM and LLD for diamond.

## Requirements

### macOS and Linux
- A C++ compiler
- Ninja
- LLD
- cmake

### Windows
- Visual Studio
- cmake

## Get LLVM
```
git clone https://github.com/llvm/llvm-project.git
```

## Change directory to LLVM
```
cd llvm-project
```

## Checkout the version you want
```
git checkout llvmorg-15.0.7
```
## Steps to build LLVM on macOS and Linux

### Configure LLVM
```
cmake -S llvm -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DLLVM_PARALLEL_{COMPILE,LINK}_JOBS=4 -DLLVM_ENABLE_PROJECTS="lld" -DLLVM_USE_LINKER=lld -DCMAKE_INSTALL_PREFIX=folder/where/you/want/to/leave/llvm
```

### Build
```
ninja
```

### Install
```
ninja install
```

### Remove unnecessary files from installation

Delete:
- All binaries, but `llvm-config` from `folder/where/you/want/to/leave/llvm/bin`
- Remove `share` folder from `folder/where/you/want/to/leave/llvm/`
- Remove all `.so` files from `folder/where/you/want/to/leave/llvm/lib`
- Remove `cmake` folder from `folder/where/you/want/to/leave/llvm/lib`

## Steps to build LLVM on Windows

## Configure LLVM

```
cmake -S llvm -B build -DLLVM_ENABLE_PROJECTS=lld -DLLVM_TARGETS_TO_BUILD=X86 -Thost=x64 -DLLVM_USE_CRT_RELEASE=MT
```

### Build

To build open the generated `LLVM.sln` file on `build` directory with Visual Studio. Select `Release` and then compile. If you don't have a lot of ram you should limit thee number of cores used in for compilation. For that you can follow this link https://stackoverflow.com/a/49068569.

### Install
```
cmake --install . --prefix folder/where/you/want/to/leave/llvm/
```

### Remove unnecessary files from installation
Delete:
- All binaries, but `llvm-config` from `folder/where/you/want/to/leave/llvm/bin`
- Remove `share` folder from `folder/where/you/want/to/leave/llvm/`
