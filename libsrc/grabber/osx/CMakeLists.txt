# Define the current source locations
SET(CURRENT_HEADER_DIR ${CMAKE_SOURCE_DIR}/include/grabber)
SET(CURRENT_SOURCE_DIR ${CMAKE_SOURCE_DIR}/libsrc/grabber/osx)

# Group the headers that go through the MOC compiler
SET(OsxGrabberQT_HEADERS
	${CURRENT_HEADER_DIR}/OsxWrapper.h
)

SET(OsxGrabberHEADERS
	${CURRENT_HEADER_DIR}/OsxFrameGrabber.h
)

SET(OsxGrabberSOURCES
	${CURRENT_SOURCE_DIR}/OsxWrapper.cpp
	${CURRENT_SOURCE_DIR}/OsxFrameGrabber.cpp
)

QT5_WRAP_CPP(OsxGrabberHEADERS_MOC ${OsxGrabberQT_HEADERS})

add_library(osx-grabber
	${OsxGrabberHEADERS}
	${OsxGrabberQT_HEADERS}
	${OsxGrabberHEADERS_MOC}
	${OsxGrabberSOURCES}
)

target_link_libraries(osx-grabber
	hyperion
	${QT_LIBRARIES})
