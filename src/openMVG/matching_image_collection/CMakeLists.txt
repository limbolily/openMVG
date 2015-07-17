
file(
  GLOB_RECURSE
  matching_collection_images_files_header
  *.hpp
)
file(
  GLOB_RECURSE
  matching_collection_images_files_cpp
  *.cpp
)
file(GLOB_RECURSE REMOVEFILESUNITTEST *_test.cpp)

#Remove the unit test files (not been used by the library)
list(REMOVE_ITEM matching_collection_images_files_cpp ${REMOVEFILESUNITTEST})

yong_add_library(openMVG_matching_image_collection
  SOURCES ${matching_collection_images_files_header}
          ${matching_collection_images_files_cpp}
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_matching_image_collection
  DEPENDENT_PROJECT cereal
    COMMIT_HASH ${CEREAL_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT eigen
    COMMIT_HASH ${EIGEN_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT flann
    COMMIT_HASH ${FLANN_HASH}
    HEADER_ONLY
  )
yong_add_library_end(openMVG_matching_image_collection)

UNIT_TEST(openMVG Pair_Builder "")
