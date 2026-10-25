cmake_minimum_required(VERSION 3.22)
project(lua-implib)

if(MSVC)
  add_custom_target(LuaLib ALL DEPENDS lua.lib)
  add_custom_command(OUTPUT lua.lib DEPENDS lua.def COMMAND ${CMAKE_AR} ${CMAKE_SHARED_LINKER_FLAGS} /def:${CMAKE_CURRENT_SOURCE_DIR}/lua.def /out:${CMAKE_CURRENT_BINARY_DIR}/lua.lib)
  install(FILES "${CMAKE_CURRENT_BINARY_DIR}/lua.lib" DESTINATION lib)
endif()
