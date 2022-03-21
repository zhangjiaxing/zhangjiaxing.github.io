Title: 生成函数调用关系图
Date: 2018-10-31 13:57:01
Category: linux
Tags: linux
Slug: gprof2dot

#### 用gprof生成函数调用关系图
1. CMakeLists.txt
```
SET(CMAKE_BUILD_TYPE "Debug")
SET(CMAKE_C_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g2 -pg -ggdb")  
SET(CMAKE_C_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
```
或
```
gcc -pg -g source.c -o binary
```

2. `./binary` 生成 gmon.out
3. `gprof ./binary> gprof_output.txt`
4. `graph2dot.py gprof_output.txt> call_graph.dot`

---------

#### valgrind 生成函数调用图 (推荐)
```
valgrind --tool=callgrind ./a.out
执行完成后在目录下生成"callgrind.out.XXX"的文件这是分析文件
gprof2dot.py -f callgrind callgrind.out.XXX > xxx.dot
```

