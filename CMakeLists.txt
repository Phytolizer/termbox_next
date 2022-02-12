cmake_minimum_required(VERSION 3.12...3.23)

project(
  termbox_next
  LANGUAGES C
  VERSION 1.1.2
  DESCRIPTION "Library for writing text-based user interfaces"
  HOMEPAGE_URL "https://github.com/nullgemm/termbox_next.git"
)

add_library(
  termbox src/input.c src/memstream.c src/ringbuffer.c src/termbox.c src/term.c
          src/utf8.c
)
add_library(termbox::termbox ALIAS termbox)
target_include_directories(termbox PUBLIC src)
install(
  TARGETS termbox
  EXPORT termbox
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES
  DESTINATION include
)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  termboxVersion.cmake
  VERSION ${PACKAGE_VERSION}
  COMPATIBILITY AnyNewerVersion
)
