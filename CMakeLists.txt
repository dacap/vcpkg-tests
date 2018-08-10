cmake_minimum_required(VERSION 3.2)
project(test)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

find_library(PIXMAN_LIBRARY NAMES pixman pixman-1)
find_path(PIXMAN_INCLUDE_DIR NAMES pixman.h PATH_SUFFIXES pixman-1)
find_package(Freetype REQUIRED)
find_package(HarfBuzz REQUIRED)

add_executable(example example.cpp)

target_include_directories(example PRIVATE
  ${PIXMAN_INCLUDE_DIR}
  ${FREETYPE_INCLUDE_DIRS}
  ${HARFBUZZ_INCLUDE_DIRS})

target_link_libraries(example PRIVATE
  ${PIXMAN_LIBRARY}
  ${FREETYPE_LIBRARIES}
  ${HARFBUZZ_LIBRARIES})
