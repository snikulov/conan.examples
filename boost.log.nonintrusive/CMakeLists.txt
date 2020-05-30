cmake_minimum_required(VERSION 3.10)
project(boost.log.nonintrusive)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(Boost 1.71.0 COMPONENTS log REQUIRED)
find_package(Threads)

set(SRC_FILES
    src/main.cpp)

add_executable(${PROJECT_NAME} ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} Boost::log_setup Boost::log Threads::Threads)
