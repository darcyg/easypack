cmake_minimum_required(VERSION 2.8)
project(test)

set(OUTPUTNAME test)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wno-deprecated -g -O2 -std=c++14")


add_definitions(-DENABLE_BOOST_SERIALIZATION)
#add_definitions(-DENABLE_MSGPACK)

aux_source_directory(. DIR_SRCS)

include_directories(${PROJECT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/..)

include_directories($ENV{BOOST_INCLUDE_PATH})
include_directories(${PROJECT_SOURCE_DIR}/../msgpack)

link_directories($ENV{BOOST_LIB_PATH})

add_executable(${OUTPUTNAME} ${DIR_SRCS})

target_link_libraries(${OUTPUTNAME} boost_serialization)
target_link_libraries(${OUTPUTNAME} boost_system)
