cmake_minimum_required(VERSION 3.0)

set(CMAKE_SYSTEM_NAME Generic)
# 工程名
project(test)

# Windows添加中文路径支持
if(WIN32)
    add_definitions(-DUNICODE -D_UNICODE)
endif()


# 选择生成方式
#set(CMAKE_BUILD_TYPE "Debug")
#set(CMAKE_BUILD_TYPE "Release")

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_definitions(-DDEBUG)
endif()

if(CMAKE_BUILD_TYPE STREQUAL "Release")
    add_definitions(-DRELEASE)
endif()

# 设定工具链
set(CMAKE_C_COMPILER gcc)
set(CMAKE_SIZE size)

# 优化等级
set(OPT "-g -O0")
#set(OPT "-O3")

# 编译标志

# 编译宏
add_definitions("-DTEST")

# 头文件路径
include_directories(
    ${PROJECT_SOURCE_DIR}/inc 
    )


######################################
# 源代码
######################################
# C 语言代码
aux_source_directory(${PROJECT_SOURCE_DIR}/src test_SRC)



#生成二进制文件
add_executable(${PROJECT_NAME} ${test_SRC} main.c)

