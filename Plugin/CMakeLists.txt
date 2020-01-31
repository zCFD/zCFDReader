paraview_add_plugin(zCFDReader
	  VERSION "1.0"
	  MODULES zCFDReader::vtkzCFDReader
	  MODULE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/Reader/vtk.module")
