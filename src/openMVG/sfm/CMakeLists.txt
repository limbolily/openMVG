
FILE(
	GLOB_RECURSE
	sfm_files_header
	*.hpp
)
FILE(
	GLOB_RECURSE
	sfm_files_cpp
	*.cpp
)
FILE(GLOB_RECURSE REMOVEFILESUNITTEST *_test.cpp)
#Remove the future main files
list(REMOVE_ITEM sfm_files_cpp ${REMOVEFILESUNITTEST})
#Remove the test header main files
FILE(GLOB_RECURSE REMOVEFILESUNITTEST *_test.hpp)
list(REMOVE_ITEM sfm_files_header ${REMOVEFILESUNITTEST})

#ADD_LIBRARY(openMVG_sfm ${sfm_files_header} ${sfm_files_cpp})
#TARGET_LINK_LIBRARIES(openMVG_sfm ceres openMVG_multiview)
yong_add_library(openMVG_sfm
  SOURCES ${sfm_files_header} ${sfm_files_cpp}
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_sfm
  DEPENDENT_LOCAL_LIBS openMVG_multiview
  DEPENDENT_PROJECT cereal
    COMMIT_HASH ${CEREAL_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT ceres
    COMMIT_HASH ${CERES_HASH}
    DEPENDENT_LIBS ceres
  DEPENDENT_PROJECT eigen
    COMMIT_HASH ${EIGEN_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT lemon
    COMMIT_HASH ${LEMON_HASH}
    HEADER_ONLY
  DEPENDENT_PROJECT osi_clp
    COMMIT_HASH ${OSI_CLP_HASH}
    HEADER_ONLY
  )
yong_add_library_end(openMVG_sfm)

#UNIT_TEST(openMVG sfm_data_io "stlplus;openMVG_features;openMVG_sfm;${openMVG_linearProgramming}")
#UNIT_TEST(openMVG sfm_data_BA
#  "openMVG_multiview_test_data;openMVG_features;openMVG_multiview;openMVG_sfm;stlplus;${openMVG_linearProgramming}")

ADD_SUBDIRECTORY(pipelines)

