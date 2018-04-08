
cmake_minimum_required (VERSION 2.6)

project (needle)
project (libneedle)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS ON)

include_directories(src/headers)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -std=c++14 -Wall")

file(GLOB SRC
    "src/*.cpp"
)


add_subdirectory (src/parser)


list(REMOVE_ITEM SRC ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp)

add_library (libneedle SHARED ${SRC})
add_executable (needle ${SRC} ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp)

target_link_libraries (libneedle parser ${PARSER_LIBRARIES})
target_link_libraries (needle libneedle)

SET_TARGET_PROPERTIES (libneedle PROPERTIES PREFIX "")
