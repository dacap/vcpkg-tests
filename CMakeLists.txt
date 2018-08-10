cmake_minimum_required(VERSION 3.11)
project(test)

find_library(PIXMAN_LIBRARY NAMES pixman pixman-1)
find_path(PIXMAN_INCLUDE_DIR NAMES pixman.h PATH_SUFFIXES pixman-1)
find_package(Freetype REQUIRED)
find_package(HarfBuzz REQUIRED)

add_executable(test test.cpp)

target_include_directories(test PRIVATE
  ${PIXMAN_INCLUDE_DIR}
  ${FREETYPE_INCLUDE_DIRS}
  ${HARFBUZZ_INCLUDE_DIRS})

target_link_libraries(test PRIVATE
  ${PIXMAN_LIBRARY}
  ${FREETYPE_LIBRARIES}
  ${HARFBUZZ_LIBRARIES})
