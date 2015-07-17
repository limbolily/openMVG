yong_add_library(openMVG_numeric
  SOURCES numeric.cpp numeric.h
  LIB_TYPE STATIC)
yong_add_dependence(openmvg openMVG_numeric
  DEPENDENT_PROJECT eigen
    COMMIT_HASH ${EIGEN_HASH}
    HEADER_ONLY
  )
yong_add_library_end(openMVG_numeric)

#ADD_LIBRARY(openMVG_numeric
#  numeric.cpp
#  numeric.h)
#SET_PROPERTY(TARGET openMVG_numeric PROPERTY FOLDER OpenMVG/OpenMVG)
#INSTALL(TARGETS openMVG_numeric DESTINATION lib/)
#
#UNIT_TEST(openMVG numeric openMVG_numeric)
#UNIT_TEST(openMVG poly openMVG_numeric)
#UNIT_TEST(openMVG lm openMVG_numeric)
