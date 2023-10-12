cmake_minimum_required(VERSION 3.23)
project(libebur128 C)

add_library(ebur128)
add_library(libebur128::ebur128 ALIAS ebur128)

target_sources(ebur128 PRIVATE ebur128/ebur128.c)
target_include_directories(ebur128 PUBLIC ${PROJECT_SOURCE_DIR})

if(WIN32)
  target_compile_definitions(ebur128 PRIVATE _USE_MATH_DEFINES=1)
  target_include_directories(ebur128 SYSTEM PRIVATE ${PROJECT_SOURCE_DIR}/queue)
endif()

find_library(MATH_LIBRARY m)
if(MATH_LIBRARY)
  target_link_libraries(ebur128 ${MATH_LIBRARY})
endif()

