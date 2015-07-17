
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

yong_add_library(openMVG_easyexif
  SOURCES exif.h exif.cpp
  LIB_TYPE STATIC)
yong_add_library_end(openMVG_easyexif)

yong_install_header_directories(openmvg
  DIRECTORIES .
  DESTINATION "third_party/easyexif"
  FILES_MATCHING PATTERN "*.h")

#if(EASYEXIF_INCLUDE_INSTALL_DIR)
#  set(INCLUDE_INSTALL_DIR ${EASYEXIF_INCLUDE_INSTALL_DIR})
#else()
#  set(INCLUDE_INSTALL_DIR "${CMAKE_INSTALL_PREFIX}/include/easyexif")
#endif()
#
#INSTALL(
#  DIRECTORY .
#  DESTINATION ${INCLUDE_INSTALL_DIR}
#  COMPONENT headers
#  FILES_MATCHING PATTERN "*.h"
#)
