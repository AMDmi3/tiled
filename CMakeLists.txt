cmake_minimum_required(VERSION 3.22 FATAL_ERROR)

project(Tiled LANGUAGES CXX VERSION 1.9.0)

option(INSTALL_HEADERS "Install header files" OFF)
option(WITH_DBUS "Enable DBus support" ON)

include(GNUInstallDirs)

add_subdirectory(src/libtiled)
add_subdirectory(src/qtpropertybrowser)
add_subdirectory(src/qtsingleapplication)
add_subdirectory(src/tiled)
add_subdirectory(src/tiledapp)
