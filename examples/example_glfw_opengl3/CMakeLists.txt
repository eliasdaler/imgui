add_executable(example_glfw_opengl3)
target_sources(example_glfw_opengl3 PUBLIC "${CMAKE_CURRENT_LIST_DIR}/main.cpp")
target_link_libraries(example_glfw_opengl3 PUBLIC
  imgui-glfw
  imgui-opengl3
)

