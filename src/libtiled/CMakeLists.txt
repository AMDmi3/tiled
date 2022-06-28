set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED YES)
set(CMAKE_CXX_EXTENSIONS NO)

find_package(ZLIB REQUIRED)
find_package(Qt5 REQUIRED COMPONENTS Gui)
set(CMAKE_AUTOMOC ON)

set(LIBTILED_SOURCES
	compression.cpp
	fileformat.cpp
	filesystemwatcher.cpp
	gidmapper.cpp
	grouplayer.cpp
	hex.cpp
	hexagonalrenderer.cpp
	imagecache.cpp
	imagelayer.cpp
	imagereference.cpp
	isometricrenderer.cpp
	layer.cpp
	logginginterface.cpp
	map.cpp
	mapformat.cpp
	mapobject.cpp
	mapreader.cpp
	maprenderer.cpp
	maptovariantconverter.cpp
	mapwriter.cpp
	minimaprenderer.cpp
	object.cpp
	objectgroup.cpp
	objecttemplate.cpp
	objecttemplateformat.cpp
	objecttypes.cpp
	orthogonalrenderer.cpp
	plugin.cpp
	pluginmanager.cpp
	properties.cpp
	propertytype.cpp
	savefile.cpp
	staggeredrenderer.cpp
	templatemanager.cpp
	tile.cpp
	tileanimationdriver.cpp
	tiled.cpp
	tilelayer.cpp
	tileset.cpp
	tilesetformat.cpp
	tilesetmanager.cpp
	varianttomapconverter.cpp
	wangset.cpp
	worldmanager.cpp
)

set(LIBTILED_HEADERS
	compression.h
	containerhelpers.h
	fileformat.h
	filesystemwatcher.h
	gidmapper.h
	grid.h
	grouplayer.h
	hex.h
	hexagonalrenderer.h
	imagecache.h
	imagelayer.h
	imagereference.h
	isometricrenderer.h
	layer.h
	logginginterface.h
	map.h
	mapformat.h
	mapobject.h
	mapreader.h
	maprenderer.h
	maptovariantconverter.h
	mapwriter.h
	minimaprenderer.h
	object.h
	objectgroup.h
	objecttemplate.h
	objecttemplateformat.h
	objecttypes.h
	orthogonalrenderer.h
	plugin.h
	pluginmanager.h
	properties.h
	propertytype.h
	qtcompat_p.h
	savefile.h
	staggeredrenderer.h
	templatemanager.h
	tile.h
	tileanimationdriver.h
	tiled.h
	tiled_global.h
	tilelayer.h
	tileset.h
	tilesetformat.h
	tilesetmanager.h
	varianttomapconverter.h
	wangset.h
	worldmanager.h
)

add_library(libtiled SHARED ${LIBTILED_SOURCES} ${LIBTILED_HEADERS})
target_include_directories(libtiled PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(libtiled Qt::Gui ZLIB::ZLIB)
set_target_properties(libtiled PROPERTIES OUTPUT_NAME tiled)
target_compile_definitions(libtiled PRIVATE
	TILED_LIBRARY
	QT_NO_CAST_FROM_ASCII
	QT_NO_CAST_TO_ASCII
	QT_NO_URL_CAST_FROM_STRING
	"QT_DISABLE_DEPRECATED_BEFORE=QT_VERSION_CHECK(5,15,0)"
	QT_NO_DEPRECATED_WARNINGS
	_USE_MATH_DEFINES
)

install(TARGETS libtiled
	RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

if(INSTALL_HEADERS)
	install(FILES ${LIBTILED_HEADERS}
		DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/tiled
	)
endif()
