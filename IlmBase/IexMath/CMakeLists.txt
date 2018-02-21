# pstanczyk@ilm.com

IF(BUILD_SHARED_LIBS)
    ADD_DEFINITIONS(-DIEXMATH_EXPORTS)
ENDIF()
ADD_LIBRARY ( IexMath ${LIB_TYPE}
  IexMathFloatExc.cpp  
  IexMathFpu.cpp
  )
TARGET_LINK_LIBRARIES(IexMath Iex)

INSTALL ( TARGETS
  IexMath
  DESTINATION
  lib
  EXPORT
  ilmbase-config
  )

TARGET_INCLUDE_DIRECTORIES ( IexMath PUBLIC
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
  IexMathFloatExc.h  
  IexMathFpu.h  
  IexMathIeeeExc.h
  DESTINATION
  include/OpenEXR
)
