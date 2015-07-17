yong_add_library(openMVG_kvld
  SOURCES kvld.cpp kvld.h algorithm.cpp algorithm.h
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_kvld
  DEPENDENT_PROJECT eigen
    COMMIT_HASH ${EIGEN_HASH}
    HEADER_ONLY
  )
yong_add_library_end(openMVG_kvld)
