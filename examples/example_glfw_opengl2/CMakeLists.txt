add_executable(example_glfw_opengl2)
target_sources(example_glfw_opengl2 PUBLIC "${CMAKE_CURRENT_LIST_DIR}/main.cpp")
target_link_libraries(example_glfw_opengl2 PUBLIC
  imgui-glfw
  imgui-opengl2
)

