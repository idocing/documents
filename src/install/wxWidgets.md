# wxWidgets

## build on windows (MinGW)
```
cd ${SRC_ROOT}/build/msw
make -f makefile.gcc CPPFLAGS=-std=c++11 SHARED=0 BUILD=debug UNICODE=1
make -f makefile.gcc CPPFLAGS=-std=c++11 SHARED=0 BUILD=release UNICODE=1
make -f makefile.gcc CPPFLAGS=-std=c++11 SHARED=1 BUILD=release UNICODE=1
```

### the library file
```
${SRC_ROOT}/lib/gcc_lib
${SRC_ROOT}/lib/gcc_dll
```