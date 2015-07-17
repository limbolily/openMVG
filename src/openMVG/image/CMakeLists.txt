
ADD_DEFINITIONS(-DTHIS_SOURCE_DIR="${CMAKE_CURRENT_SOURCE_DIR}")

file(
	GLOB_RECURSE
	image_files_header
	*.hpp
)
file(
	GLOB_RECURSE
	image_files_cpp
	*.cpp
)
file(GLOB_RECURSE REMOVEFILESUNITTEST *_test.cpp)

#Remove the future main files
list(REMOVE_ITEM image_files_cpp ${REMOVEFILESUNITTEST})

yong_add_library(openMVG_image
  SOURCES ${image_files_header} ${image_files_cpp}
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_image
  DEPENDENT_LOCAL_LIBS openMVG_numeric
  DEPENDENT_PROJECT eigen
    COMMIT_HASH ${EIGEN_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT jpeg_turbo
    COMMIT_HASH ${JPEG_TURBO_HASH}
    DEPENDENT_LIBS jpeg_turbo
  DEPENDENT_PROJECT png
    COMMIT_HASH ${PNG_HASH}
    DEPENDENT_LIBS png
  DEPENDENT_PROJECT tiff
    COMMIT_HASH ${TIFF_HASH}
    DEPENDENT_LIBS tiff)
yong_add_library_end(openMVG_image)

UNIT_TEST(openMVG image "openMVG_image")
UNIT_TEST(openMVG image_drawing "openMVG_image")
UNIT_TEST(openMVG image_io "openMVG_image")
UNIT_TEST(openMVG image_filtering "openMVG_image")

