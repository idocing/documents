# cmake

## notes
```
# notes
```

## command
```
command(arg1 arg2 ...)
```

## var
```
set(FOO abc)
command(${FOO}) //command(abc)
command("${FOO}") //command("abc")
```

## flow control
```
if()...else()/elseif()...endif()
while()...endwhile()
foreach()...endforeach()
```

## command list
```
include_directories("dir1" "dir2" ...) //-Idir1 -Idir2
link_directories("dir1" "dir2")
aux_source_directory("source-dir" variable)
add_executable()
add_library()
add_custom_target()
add_dependencies(target1 t2 t3)
add_definitions("-Wall -ansi")
target_link_libraries(target-name lib1 lib2 ...)
link_libraries(lib1 lib2 ...)
set_target_properties(...)
message(...)
install(files "f1" "f2" destination)
set(variable value)
list(append|insert|length|get|remove_item|remove_at|sort ...)
string(toupper|tolower|length|substring|replace|regex ...)
separate_arguments(variable)
file(write|read|append|glob|glob_recurse|remove|make_directory ...)
find_file()
find_path()
find_library()
find_program()
find_package()
exec_program(bin [work_dir] args <..> [output_variable var] [return_value var])
option(option_var "description" [initial value])
```

## variable

### project path
```
CMAKE_SOURCE_DIR
PROJECT_SOURCE_DIR
<projectname>_SOURCE_DIR
```

### root path
```
CMAKE_BINARY_DIR
PROJECT_BINARY_DIR
<projectname>_BINARY_DIR
```

### current path
```
CMAKE_CURRENT_SOURCE_DIR
CMAKE_CURRENT_BINARY_DIR
CMAKE_CURRENT_LIST_FILE
```

### CMakeLists.txt path
```
CMAKE_BUILD_TYPE
```

## debug or release
```
set(CMAKE_BUILD_TYPE Debug)
cmake DCMAKE_BUILD_TYPE=Release
```

## build args
```
CMAKE_C_FLAGS
CMAKE_CXX_FLAGS
CMAKE_INCLUDE_PATH
CMAKE_LIBRARY_PATH
CMAKE_MODULE_PATH
CMAKE_INSTALL_PREFIX
BUILD_SHARED_LIBS
```

## example 1
```
cmake_minimum_required(VERSION 3.0)
project(c_demo)

include_directories(header)
set(SRC src/main.cpp)
aux_source_directory(src SRC)
add_executable(c_demo ${SRC})
```

# cmake
## INCLUDE_DIRECTORIES
```
include_directories("/xxx/include")
export CPLUS_INCLUDE_PATH=CPLUS_INCLUDE_PATH:/xxx/include
```

## LINK_DIRECTORIES
```
link_directories(directory1 directory2 ...)
```

```
LINK_DIRECTORIES("/xxx/lib")
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/xxx/lib
```

## LINK_LIBRARIES
```
LINK_LIBRARIES("/xxx/lib/libeng.so")
```
or
```
LINK_LIBRARIES("/xxx/lib/libeng.so"　"/xxx/lib/libmx.so")
```


## TARGET_LINK_LIBRARIES
```
TARGET_LINK_LIBRARIES(targetlibrary1 <debug | optimized> library2 ..)
```

```
TARGET_LINK_LIBRARIES(myProject hello)
TARGET_LINK_LIBRARIES(myProject libhello.a)
TARGET_LINK_LIBRARIES(myProject libhello.so)
```
or
```
TARGET_LINK_LIBRARIES(myProject libeng.so)
TARGET_LINK_LIBRARIES(myProject eng)
TARGET_LINK_LIBRARIES(myProject -leng)
```

## example
```
cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
 
include_directories("/xxx/include")
 
#directly link to the libraries.
link_libraries("/xxx/lib/libeng.so")
link_libraries("/xxx/lib/libmx.so")
 
#equals to below
link_libraries("/xxx/lib/libeng.so" "/xxx/lib/libmx.so")
 
add_executable(myProject main.cpp) 
```

```
cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
 
include_directories("/xxx/include")

link_directories("/xxx/lib")
 
add_executable(myProject main.cpp)
 
target_link_libraries(myProject eng mx)
 
#equals to below
#target_link_libraries(myProject -leng -lmx)
#target_link_libraries(myProject libeng.so libmx.so)
```
