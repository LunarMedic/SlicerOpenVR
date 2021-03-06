project(qSlicer${MODULE_NAME}ModuleWidgets)

set(KIT ${PROJECT_NAME})

#-----------------------------------------------------------------------------
find_package(VTK COMPONENTS vtkRenderingOpenVR REQUIRED)

#-----------------------------------------------------------------------------
set(${KIT}_EXPORT_DIRECTIVE "Q_SLICER_QTMODULES_${MODULE_NAME_UPPER}_WIDGETS_EXPORT")

set(${KIT}_INCLUDE_DIRECTORIES
  ${vtkSlicerVRModuleMRML_INCLUDE_DIRS}
  ${VTK_INCLUDE_DIRS}
  )

set(${KIT}_SRCS
  qMRMLVRView.cxx
  qMRMLVRView_p.h
  qMRMLVRView.h
  )

set(${KIT}_MOC_SRCS
  qMRMLVRView.h
  qMRMLVRView_p.h
  )

set(${KIT}_UI_SRCS
  )

set(${KIT}_RESOURCES
  )

set(${KIT}_TARGET_LIBRARIES
  vtkSlicer${MODULE_NAME}ModuleMRML
  ${VTK_LIBRARIES}
  )

#-----------------------------------------------------------------------------
SlicerMacroBuildModuleWidgets(
  NAME ${KIT}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT_DIRECTIVE}
  INCLUDE_DIRECTORIES ${${KIT}_INCLUDE_DIRECTORIES}
  SRCS ${${KIT}_SRCS}
  MOC_SRCS ${${KIT}_MOC_SRCS}
  UI_SRCS ${${KIT}_UI_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  RESOURCES ${${KIT}_RESOURCES}
  WRAP_PYTHONQT
  )

#-----------------------------------------------------------------------------
#add_subdirectory(DesignerPlugins)

# Testing
if(BUILD_TESTING)
#  add_subdirectory(Testing)
endif()

