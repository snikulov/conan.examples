cmake_minimum_required(VERSION 3.10)
project(boost.log.intrusive.conan)

#
# Don't forget to use libstdc++11 in profile by issuing
# $ conan profile update settings.compiler.libcxx=libstdc++11 default
#
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Include conan stuff explicitly
# it will update all paths for us
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)

# I don't want to place my binary into ${CMAKE_BINARY_DIR}/bin
# so I enforce conan do not alter RUNTIME paths
conan_basic_setup(TARGETS NO_OUTPUT_DIRS)

find_package(Boost 1.71.0 COMPONENTS log REQUIRED)
find_package(Threads)

# Add your files here...
set(SRC_FILES
  src/main.cpp
  )

add_executable(${PROJECT_NAME} ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} Boost::log_setup Boost::log Threads::Threads)
