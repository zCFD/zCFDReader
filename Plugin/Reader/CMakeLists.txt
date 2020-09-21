set(classes
	vtkzCFDReader)

set(private_headers "")

vtk_module_find_package(
  PACKAGE Boost
  VERSION 1.50
  COMPONENTS python)

vtk_module_find_package(
  PACKAGE Python3)

vtk_module_find_package(
  PACKAGE hdf5 )

MESSAGE(STATUS "ZCFDREADER: ${HDF5_hdf5_LIBRARIES}")

# get_cmake_property(_variableNames VARIABLES)
# list (SORT _variableNames)
# foreach (_variableName ${_variableNames})
#    message(STATUS "${_variableName}=${${_variableName}}")
# endforeach()


vtk_module_add_module(zCFDReader::vtkzCFDReader
  CLASSES ${classes}
  PRIVATE_HEADERS ${private_headers})

vtk_module_link(zCFDReader::vtkzCFDReader PUBLIC ${HDF5_hdf5_LIBRARIES})

paraview_add_server_manager_xmls(
	XMLS  zCFDReader.xml)
