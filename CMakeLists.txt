cmake_minimum_required(VERSION 3.10)
project(Heco VERSION 0.1.0 LANGUAGES C CXX)

file(GLOB LIB_SOURCES
    "src/*.cpp"
)
add_library(Heco Heco.cpp)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

add_library(Hecodll STATIC ${LIB_SOURCES})


include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include_directories(inc)
include(CPack)

add_executable(Main scripts/main.cpp)
target_link_libraries(Main Hecodll)
