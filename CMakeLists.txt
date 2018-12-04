cmake_minimum_required(VERSION 3.7.2)
project(helloWorld)
#file(GLOB SOURCES "/usr/xenomai/include/alchemy/*.*")
include_directories(/usr/xenomai/include/alchemy/)
include_directories(/usr/xenomai/include/)
include_directories(/usr/xenomai/cobalt/)
include_directories(/usr/xenomai/boilerplate/)

execute_process(COMMAND /usr/xenomai/bin/xeno-config --skin=native --cflags OUTPUT_VARIABLE XENO_NATIVE_CFLAGS OUTPUT_STRIP_TRAILING_WHITESPACE)
execute_process(COMMAND /usr/xenomai/bin/xeno-config --skin=native --ldflags OUTPUT_VARIABLE XENO_NATIVE_LDFLAGS OUTPUT_STRIP_TRAILING_WHITESPACE)


SET(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -g -Wall -O3 ${XENO_NATIVE_CFLAGS} -DHAVE_SOCKLEN_T")

add_executable(helloWorld helloWorld.c)
