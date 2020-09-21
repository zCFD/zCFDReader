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

vtk_module_add_module(zCFDReader::vtkzCFDReader
  CLASSES ${classes}
  PRIVATE_HEADERS ${private_headers})

paraview_add_server_manager_xmls(
	XMLS  zCFDReader.xml)
