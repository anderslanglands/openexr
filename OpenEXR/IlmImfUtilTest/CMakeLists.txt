
# IlmImfUtilTest

LINK_DIRECTORIES ( ${CMAKE_CURRENT_BINARY_DIR}/../IlmImf )


ADD_EXECUTABLE ( IlmImfUtilTest
  main.cpp
  testFlatImage.cpp
  testDeepImage.cpp
  testIO.cpp
 )


ADD_TEST ( TestIlmImfUtil IlmImfUtilTest )
TARGET_LINK_LIBRARIES ( IlmImfUtilTest 
        IlmImfUtil
        IlmImf  
        IlmBase::Half 
        IlmBase::Iex
        IlmBase::Imath
        IlmBase::IlmThread
        ${PTHREAD_LIB} ${ZLIB_LIBRARIES}
        )

