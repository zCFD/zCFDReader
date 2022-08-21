cmake_minimum_required(VERSION 3.8)
project(zCFDReader)
include(GNUInstallDirs)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_BINDIR}")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR}")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_LIBDIR}")
set(BUILD_SHARED_LIBS ON)
set(CMAKE_INSTALL_RPATH "\$ORIGIN")
find_package(Boost 1.50 REQUIRED COMPONENTS python)
find_package(hdf5 REQUIRED)
find_package(Python REQUIRED)
find_package(ParaView REQUIRED)
paraview_plugin_scan(
	  PLUGIN_FILES "${CMAKE_CURRENT_SOURCE_DIR}/Plugin/paraview.plugin"
          PROVIDES_PLUGINS plugins
	  ENABLE_BY_DEFAULT ON)
paraview_plugin_build(
        LIBRARY_DESTINATION "${CMAKE_INSTALL_BINDIR}"
        LIBRARY_SUBDIRECTORY "plugins"
	PLUGINS_FILE_NAME "zCFDReader.plugin.xml"
	TARGET plugins
	AUTOLOAD ${plugins}
	PLUGINS ${plugins})
