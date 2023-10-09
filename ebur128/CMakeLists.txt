cmake_minimum_required(VERSION 3.23)
project(ebur128)

add_library(ebur128 ebur128.c)

if(WIN32)
  include_directories(SYSTEM queue)
  target_compile_definitions(ebur128 PUBLIC _USE_MATH_DEFINES=1)
endif()

find_library(MATH_LIBRARY m)
if(MATH_LIBRARY)
  target_link_libraries(ebur128 ${MATH_LIBRARY})
endif()
