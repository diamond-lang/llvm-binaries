# LLVM binaries
Prebuilt versions of LLVM and LLD for diamond.

## Requirements
- A C++ compiler
- Ninja
- LLD

## Steps to build LLVM (macOS and Linux)

### Get LLVM
```
git clone [LLVM]([url](https://github.com/llvm/llvm-project)https://github.com/llvm/llvm-project).
```

### Change directory to LLVM
```
cd llvm-project
```

### Checkout the version you want
```
git checkout llvmorg-15.0.7
```

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
