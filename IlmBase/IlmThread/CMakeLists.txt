# yue.nicholas@gmail.com

SET( ILMTHREAD_LIBRARY_SOURCES
  IlmThread.cpp
  IlmThreadMutex.cpp
  IlmThreadMutexPosix.cpp
  IlmThreadPool.cpp
  IlmThreadPosix.cpp
  IlmThreadSemaphore.cpp
  IlmThreadSemaphorePosixCompat.cpp
  IlmThreadSemaphorePosix.cpp
)
IF (WIN32)
  SET( ILMTHREAD_LIBRARY_SOURCES ${ILMTHREAD_LIBRARY_SOURCES}
    IlmThreadMutexWin32.cpp
    IlmThreadSemaphoreWin32.cpp
    IlmThreadWin32.cpp
	)
ENDIF()


IF(BUILD_SHARED_LIBS)
  ADD_DEFINITIONS(-DILMTHREAD_EXPORTS)
ENDIF()

ADD_LIBRARY ( IlmThread ${LIB_TYPE}
  ${ILMTHREAD_LIBRARY_SOURCES}
  )
TARGET_LINK_LIBRARIES(IlmThread Iex)

INSTALL ( TARGETS
  IlmThread
  DESTINATION
  lib
  EXPORT
  ilmbase-config
  )

TARGET_INCLUDE_DIRECTORIES ( IlmThread PUBLIC
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
  IlmThreadPool.h
  IlmThread.h
  IlmThreadSemaphore.h
  IlmThreadMutex.h
  IlmThreadNamespace.h
  IlmThreadExport.h
  IlmThreadForward.h
  DESTINATION
  include/OpenEXR
)
