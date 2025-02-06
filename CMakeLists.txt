cmake_minimum_required(VERSION 3.10)
project(unity_jni_loader)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Find JNI package
find_package(JNI REQUIRED)

# Add JNI include directory
include_directories(${JNI_INCLUDE_DIRS})

# Add main.cpp as source file
set(SOURCE_FILES main.cpp)

# Define the output library name
set(LIB_NAME "main")

# Add shared library target
add_library(${LIB_NAME} SHARED ${SOURCE_FILES})

# Link JNI library
target_link_libraries(${LIB_NAME} ${JNI_LIBRARIES})

# Android specific settings
set(CMAKE_SYSTEM_NAME Android)
set(CMAKE_ANDROID_ARCH_ABI arm64-v8a)
set(CMAKE_ANDROID_NDK $ENV{ANDROID_NDK_HOME})
set(CMAKE_ANDROID_STL_TYPE c++_shared)
set(CMAKE_ANDROID_NDK_TOOLCHAIN_VERSION clang)
