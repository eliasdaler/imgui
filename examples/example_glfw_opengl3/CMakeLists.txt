add_executable(example_glfw_opengl3)
target_sources(example_glfw_opengl3 PUBLIC "${CMAKE_CURRENT_LIST_DIR}/main.cpp")
target_link_libraries(example_glfw_opengl3 PUBLIC
  imgui-glfw
  imgui-opengl3
)

if(WIN32)
  get_target_property(GLFW3_BUILD_TYPE glfw TYPE)
  if (GLFW3_BUILD_TYPE STREQUAL SHARED_LIBRARY)
    add_custom_command(TARGET example_glfw_opengl3 POST_BUILD
      COMMAND ${CMAKE_COMMAND} -E copy_if_different
          $<TARGET_FILE:glfw>
          $<TARGET_FILE_DIR:example_glfw_opengl3>
	)
  endif()
endif()
