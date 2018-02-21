# yue.nicholas@gmail.com

IF(BUILD_SHARED_LIBS)
    ADD_DEFINITIONS(-DIEX_EXPORTS)
ENDIF()

ADD_LIBRARY ( Iex ${LIB_TYPE}
  IexBaseExc.cpp
  IexThrowErrnoExc.cpp
  )


INSTALL ( TARGETS
  Iex
  DESTINATION
  lib
  EXPORT
  ilmbase-config
  )

TARGET_INCLUDE_DIRECTORIES ( Iex PUBLIC
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
  IexBaseExc.h
  IexMathExc.h
  IexThrowErrnoExc.h
  IexErrnoExc.h
  IexMacros.h
  Iex.h
  IexNamespace.h
  IexExport.h
  IexForward.h
  DESTINATION
  include/OpenEXR
)
