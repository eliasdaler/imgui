cmake_minimum_required(VERSION 3.8.2)

project(imgui
  VERSION 1.82
  LANGUAGES C CXX
)

option(IMGUI_BACKEND_OPENGL2 "Build OpenGL 2 backend" ON)
option(IMGUI_BACKEND_OPENGL3 "Build OpenGL 3 backend" ON)
option(IMGUI_BACKEND_SDL "Build SDL backend" ON)
option(IMGUI_BACKEND_GLFW "Build GLFW backend" ON)

option(IMGUI_BUILD_EXAMPLES "Build examples" ON)

option(IMGUI_DEMO "Build imgui_demo.cpp" ON)

set(IMGUI_HEADERS
  "${CMAKE_CURRENT_LIST_DIR}/imgui.h"
  "${CMAKE_CURRENT_LIST_DIR}/imgui_internal.h"
)

set(IMGUI_STB_HEADERS
  "${CMAKE_CURRENT_LIST_DIR}/imstb_rectpack.h"
  "${CMAKE_CURRENT_LIST_DIR}/imstb_textedit.h"
  "${CMAKE_CURRENT_LIST_DIR}/imstb_truetype.h"
)

set(IMGUI_SOURCES
  "${CMAKE_CURRENT_LIST_DIR}/imgui.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/imgui_draw.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/imgui_tables.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/imgui_widgets.cpp"
)

if(IMGUI_DEMO)
  list(APPEND IMGUI_SOURCES "${CMAKE_CURRENT_LIST_DIR}/imgui_demo.cpp")
endif()

add_library(imgui INTERFACE)
target_sources(imgui INTERFACE
  ${IMGUI_SOURCES}
  ${IMGUI_HEADERS}
  ${IMGUI_STB_HEADERS}
)
target_include_directories(imgui INTERFACE "${CMAKE_CURRENT_LIST_DIR}")

if(IMGUI_BACKEND_OPENGL3 AND (NOT CMAKE_SYSTEM_NAME STREQUAL Emscripten))
  add_subdirectory(examples/libs/gl3w)
endif()

add_subdirectory(backends)

if(IMGUI_BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
