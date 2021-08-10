# Segger RTT printf implementation module

file(GLOB_RECURSE sources CONFIGURE_DEPENDS
  "${CMAKE_CURRENT_SOURCE_DIR}/src/*.c"
  "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
)

file(GLOB_RECURSE headers CONFIGURE_DEPENDS
  "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/*.hpp"
)

set_source_files_properties(${sources} PROPERTIES LANGUAGE CXX)
set_source_files_properties(${headers} PROPERTIES LANGUAGE CXX)

add_library(printf_impl_SeggerRTT ${sources})
target_include_directories(printf_impl_SeggerRTT PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)

target_precompile_headers(
  printf_impl_SeggerRTT
  PUBLIC
  <stddef.h>
  <stdint.h>
  <stdbool.h>
  <string.h>
)