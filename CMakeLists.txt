cmake_minimum_required(VERSION 3.22)
project(lua-implib)
add_custom_command(
	OUTPUT lua.lib
	COMMAND ${CMAKE_AR} ${CMAKE_SHARED_LINKER_FLAGS}
		/def:${CMAKE_CURRENT_SOURCE_DIR}/lua.def
		/out:lua.lib
	DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/lua.def
)
add_custom_target(lua-implib ALL DEPENDS lua.lib)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/lua.lib DESTINATION lib)
