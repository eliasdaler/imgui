add_executable(example_sdl_opengl2)
target_sources(example_sdl_opengl2 PUBLIC "${CMAKE_CURRENT_LIST_DIR}/main.cpp")
target_link_libraries(example_sdl_opengl2 PUBLIC
  imgui-sdl
  imgui-opengl2
)

