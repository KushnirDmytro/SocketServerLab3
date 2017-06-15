cmake_minimum_required(VERSION 3.6)
project(socket_server)

SET(CMAKE_CXX_FLAGS  "-pthread")

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES clientTCP.cpp ${GCC_COVERAGE_LINK_FLAGS})

add_executable(clientTCP ${SOURCE_FILES})
set(SOURCE_FILES ServerBoost.cpp ${GCC_COVERAGE_LINK_FLAGS})

add_executable(serverBoost ${SOURCE_FILES})



FIND_PACKAGE( Boost COMPONENTS filesystem program_options system thread REQUIRED )
set(CMAKE_VERBOSE_MAKEFILE ON)

link_directories(${Boost_LIBRARY_DIR})
INCLUDE_DIRECTORIES( ${Boost_INCLUDE_DIR} )

target_link_libraries( serverBoost ${Boost_LIBRARIES} )

target_link_libraries( clientTCP ${Boost_LIBRARIES} )

