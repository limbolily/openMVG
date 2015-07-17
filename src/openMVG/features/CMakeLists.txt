
#project(features)

file(
	GLOB_RECURSE
	features_files_headers
	*.hpp
)

file(
	GLOB_RECURSE
	features_files_sources
	*.cpp
)

file(GLOB_RECURSE REMOVEFILESUNITTEST *_test.cpp)
#Remove the future main files
list(REMOVE_ITEM features_files_sources ${REMOVEFILESUNITTEST})
			
set_source_files_properties(${features_files_sources} PROPERTIES LANGUAGE CXX)
#ADD_LIBRARY(openMVG_features ${features_files_sources} ${features_files_headers})
yong_add_library(openMVG_features
  SOURCES ${features_files_sources} ${features_files_headers}
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_features
  DEPENDENT_PROJECT cereal
    COMMIT_HASH ${CEREAL_HASH}
    HEADER_ONLY
    DEPENDENT_PROJECT eigen
      COMMIT_HASH ${EIGEN_HASH}
      HEADER_ONLY
  )
yong_add_library_end(openMVG_features)

#UNIT_TEST(openMVG features "openMVG_features")

