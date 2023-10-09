cmake_minimum_required(VERSION 3.23)
project(ebur128)

if(WIN32)
  include_directories(SYSTEM queue)
endif()

add_library(ebur128 ebur128.c)
set_target_properties(ebur128 PROPERTIES SOVERSION 1 VERSION 1.2.6)

find_library(MATH_LIBRARY m)
if(MATH_LIBRARY)
  target_link_libraries(ebur128 ${MATH_LIBRARY})
endif()
