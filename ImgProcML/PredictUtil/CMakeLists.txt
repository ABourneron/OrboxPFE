cmake_minimum_required(VERSION 3.2)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++1y")

find_program(CMAKE_C_COMPILER NAMES $ENV{CC} gcc PATHS ENV PATH NO_DEFAULT_PATH)
find_program(CMAKE_CXX_COMPILER NAMES $ENV{CXX} g++ PATHS ENV PATH NO_DEFAULT_PATH)

project(PredictUtil)

find_package(OpenCV REQUIRED)
add_subdirectory(../Common shared_lib)

include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(${SHARED_LIB_INCLUDE_DIR})

set(SOURCE_FILES main.cpp)

add_executable(predictUtil ${SOURCE_FILES})

target_link_libraries(predictUtil shared_lib)
target_link_libraries(predictUtil ${OpenCV_LIBS})