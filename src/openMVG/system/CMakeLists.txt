
file(
  GLOB_RECURSE
  system_files_header
  *.hpp
)
file(
  GLOB_RECURSE
  system_files_cpp
  *.cpp
)

yong_add_library(openMVG_system
  SOURCES ${system_files_header} ${system_files_cpp}
  LIB_TYPE STATIC)
yong_add_library_end(openMVG_system)
