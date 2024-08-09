# sample

## project name 
```
project(project_name)
```

## version required
```
cmake_minimum_required(VERSION 3.0)
```

## set source dir
```
aux_source_directory(<dir> <variable>)
aux_source_directory(. DIR_SRCS)
```

## add subdirectory
```
add_subdirectory(<dir>)
```

## add static library
```
add_library(lib_name STATIC source_list)
```

## add shared library
```
add_library(lib_name SHARED source_list)
```

## add executable
```
add_executable(exe_name source_list)
```

## link library
```
target_link_libraries(exe_name lib_name)
```