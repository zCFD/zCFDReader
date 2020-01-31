set(classes
	vtkzCFDReader)

set(private_headers "")

vtk_module_find_package(
  PACKAGE Boost
  VERSION 1.50
  COMPONENTS python)

vtk_module_find_package(
  PACKAGE Python3)

vtk_module_add_module(zCFDReader::vtkzCFDReader
  CLASSES ${classes}
  PRIVATE_HEADERS ${private_headers})

#vtk_module_include(zCFDReader::vtkzCFDReader
#	           PRIVATE 
#		   /gpfs/zenotech/home/jappa/workarea/poly/python3/zCFD/INSTALL/icc_sse_impi/include/python3.7m
#		   )

vtk_module_link(zCFDReader::vtkzCFDReader)

paraview_add_server_manager_xmls(
	XMLS  zCFDReader.xml)
