set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED YES)
set(CMAKE_CXX_EXTENSIONS NO)

find_package(Qt5 REQUIRED COMPONENTS Widgets Network)
set(CMAKE_AUTOMOC ON)

set(QTSINGLEAPPLICATION_SOURCES
	src/qtlocalpeer.cpp
	src/qtsingleapplication.cpp
)

set(QTSINGLEAPPLICATION_HEADERS
	src/qtlocalpeer.h
	src/qtsingleapplication.h
)

add_library(qtsingleapplication OBJECT ${QTSINGLEAPPLICATION_SOURCES} ${QTSINGLEAPPLICATION_HEADERS})
target_include_directories(qtsingleapplication PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_link_libraries(qtsingleapplication PUBLIC Qt::Widgets Qt::Network)
