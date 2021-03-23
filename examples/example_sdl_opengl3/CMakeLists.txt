add_executable(example_sdl_opengl3)
target_sources(example_sdl_opengl3 PUBLIC "${CMAKE_CURRENT_LIST_DIR}/main.cpp")
target_link_libraries(example_sdl_opengl3 PUBLIC
  imgui-sdl
  imgui-opengl3
)

if(WIN32)
  # target_link_libraries(example_sdl_opengl3 PUBLIC SDL2main)
  add_custom_command(TARGET example_sdl_opengl3 POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        $<TARGET_FILE:SDL2>
        $<TARGET_FILE_DIR:example_sdl_opengl3>)
endif()