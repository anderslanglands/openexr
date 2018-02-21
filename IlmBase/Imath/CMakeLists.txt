# yue.nicholas@gmail.com

IF(BUILD_SHARED_LIBS)
    ADD_DEFINITIONS(-DIMATH_EXPORTS)
ENDIF()

ADD_LIBRARY ( Imath ${LIB_TYPE}
  ImathBox.cpp
  ImathRandom.cpp
  ImathColorAlgo.cpp
  ImathShear.cpp
  ImathFun.cpp
  ImathVec.cpp
  ImathMatrixAlgo.cpp
)
TARGET_LINK_LIBRARIES(Imath Iex)


INSTALL ( TARGETS
  Imath
  DESTINATION
  lib
  EXPORT
  ilmbase-config
  )

TARGET_INCLUDE_DIRECTORIES ( Imath PUBLIC
  $<INSTALL_INTERFACE:include>
  # Horrible hack to get OpenEXR to build correctly
  $<INSTALL_INTERFACE:include/OpenEXR>
  )

INSTALL ( EXPORT
  ilmbase-config
  NAMESPACE IlmBase::
  DESTINATION cmake
  )

INSTALL ( FILES 
  ImathBoxAlgo.h
  ImathBox.h
  ImathColorAlgo.h
  ImathColor.h
  ImathEuler.h
  ImathExc.h
  ImathExport.h
  ImathForward.h
  ImathFrame.h
  ImathFrustum.h
  ImathFrustumTest.h
  ImathFun.h
  ImathGL.h
  ImathGLU.h
  ImathHalfLimits.h
  ImathInt64.h
  ImathInterval.h
  ImathLimits.h
  ImathLineAlgo.h
  ImathLine.h
  ImathMath.h
  ImathMatrixAlgo.h
  ImathMatrix.h
  ImathNamespace.h
  ImathPlane.h
  ImathPlatform.h
  ImathQuat.h
  ImathRandom.h
  ImathRoots.h
  ImathShear.h
  ImathSphere.h
  ImathVecAlgo.h
  ImathVec.h
  DESTINATION
  include/OpenEXR
)
