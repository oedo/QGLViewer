cmake_minimum_required(VERSION 3.14)

project(QGLViewer)

find_package(Qt6 COMPONENTS Core Gui OpenGLWidgets REQUIRED)

SET(SOURCES
  camera.cpp
  camera.h
  gldata.cpp
  gldata.h
  qglviewer.cpp
  qglviewer.h
)

add_executable(QGLViewerExample main.cpp)
target_link_libraries(QGLViewerExample ${PROJECT_NAME})

add_library(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME}
  Qt6::Core
  Qt6::Gui
  Qt6::OpenGLWidgets
)

set_target_properties(${PROJECT_NAME} PROPERTIES
    LINKER_LANGUAGE CXX
    AUTOMOC ON
)

target_compile_features(${PROJECT_NAME} PUBLIC
  cxx_nonstatic_member_init
)
