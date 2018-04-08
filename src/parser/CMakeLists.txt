
cmake_minimum_required (VERSION 2.6)

project (parser)

file(GLOB SRC
    "*.cpp"
)


add_library (parser STATIC ${SRC})

set (CORELIBRARY_LIBRARIES )

target_link_libraries (parser ${PARSER_LIBRARIES})
