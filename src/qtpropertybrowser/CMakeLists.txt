set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED YES)
set(CMAKE_CXX_EXTENSIONS NO)

find_package(Qt5 REQUIRED COMPONENTS Widgets)
set(CMAKE_AUTOMOC ON)

set(QTPROPERTYBROWSER_SOURCES
	src/qtbuttonpropertybrowser.cpp
	src/qteditorfactory.cpp
	src/qtgroupboxpropertybrowser.cpp
	src/qtpropertybrowser.cpp
	src/qtpropertybrowserutils.cpp
	src/qtpropertymanager.cpp
	src/qttreepropertybrowser.cpp
	src/qtvariantproperty.cpp
)

set(QTPROPERTYBROWSER_HEADERS
	src/qtbuttonpropertybrowser.h
	src/qteditorfactory.h
	src/qtgroupboxpropertybrowser.h
	src/qtpropertybrowser.h
	src/qtpropertybrowserutils_p.h
	src/qtpropertymanager.h
	src/qttreepropertybrowser.h
	src/qtvariantproperty.h
)

add_library(qtpropertybrowser OBJECT ${QTPROPERTYBROWSER_SOURCES} ${QTPROPERTYBROWSER_HEADERS})
target_include_directories(qtpropertybrowser PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_link_libraries(qtpropertybrowser PUBLIC Qt::Widgets)
