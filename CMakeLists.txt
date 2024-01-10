cmake_minimum_required(VERSION 3.13)

set(CMAKE_CXX_STANDARD 17)

project(imguizmo DESCRIPTION "Immediate mode 3D gizmo for scene editing and other controls based on Dear Imgui")

find_package(imgui QUIET PATHS ${IMGUI_ROOT})

option(BUILD_SHARED_LIBS "Build shared libs" OFF)

# Create the main target
add_library(${PROJECT_NAME} 
    GraphEditor.cpp
    ImCurveEdit.cpp
    ImGradient.cpp
    ImGuizmo.cpp
    ImSequencer.cpp)

target_include_directories(${PROJECT_NAME}
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:ImGuizmo.h>
    $<INSTALL_INTERFACE:GraphEditor.h>
    $<INSTALL_INTERFACE:ImCurveEdit.h>
    $<INSTALL_INTERFACE:ImGradient.h>
    $<INSTALL_INTERFACE:ImGuizmo.h>
    $<INSTALL_INTERFACE:ImSequencer.h>
    $<INSTALL_INTERFACE:ImZoomSlider.h>
  PRIVATE
    ${IMGUI_ROOT})

target_link_libraries(${PROJECT_NAME}
    PUBLIC
        imgui)
        