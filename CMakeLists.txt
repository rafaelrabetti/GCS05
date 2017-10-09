cmake_minimum_required (VERSION 3.9.2)

project(poke CXX)
set(INCLUDES_PATH "${PROJECT_SOURCE_DIR}/includes/")
set(SOURCES_PATH "${PROJECT_SOURCE_DIR}/sources/")
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
	set (pokedex_VERSION_MAJOR 1)
	set (pokedex_VERSION_MINOR 0)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
	set (pokedex_VERSION_MAJOR 2)
	set (pokedex_VERSION_MINOR 1)
endif()
include_directories(INCLUDES_PATH)

configure_file (
  "${INCLUDES_PATH}/version.hpp.in"
  "${PROJECT_BINARY_DIR}/version.hpp"
)

file(GLOB_RECURSE SOURCES "${SOURCES_PATH}/*.cpp")

add_executable(poke ${SOURCES_PATH})
set_target_properties(poke PROPERTIES LINKER_LANGUAGE CXX)