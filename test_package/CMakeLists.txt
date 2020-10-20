cmake_minimum_required(VERSION 3.1.0)
project(test_package)

option(LIBASYNC_STATIC "Include Async++ as a static library" OFF)

find_package(Threads)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

if (LIBASYNC_STATIC)
    add_compile_definitions(LIBASYNC_STATIC)
endif()

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS} ${CMAKE_THREAD_LIBS_INIT})
