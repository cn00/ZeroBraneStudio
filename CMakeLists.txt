cmake_minimum_required(VERSION 3.0)

project(zbs C)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -DLUAINTF_LINK_LUA_COMPILED_IN_CXX=0 -DLUAINTF_HEADERS_ONLY=1 -DENV_HAVE_WCTYPE_H=1")

add_subdirectory(lua)
add_subdirectory(lfs)
add_subdirectory(lpeg)
# add_subdirectory(luasec)
add_subdirectory(luasocket)
add_subdirectory(scintillua)
add_subdirectory(wxWidgets)

add_subdirectory(p7zip)


set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DLUA_USE_LINUX -DLUA_USE_DLOPEN")

set(wxLua_LUA_LIBRARY_USE_BUILTIN FALSE)
set(wxLua_LUA_ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lua)
set(wxLua_LUA_INCLUDE_DIR "${wxLua_LUA_ROOT_DIR}/src")
set(wxLua_LUA_LIBRARY "${CMAKE_BINARY_DIR}/lua/$(CONFIGURATION)/liblua.dylib")
add_subdirectory(wxlua/wxLua)