cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

project(libmicrorl VERSION 0.1 LANGUAGES C)

add_library(
    microrl
    STATIC
    src/microrl.c)

set_property(
    TARGET
    microrl
    PROPERTY
    C_STANDARD
    99)

target_compile_options(
    microrl
    PRIVATE
    -Wall
    -Wextra
    -Wshadow
    -Wno-unused-parameter
    -Wwrite-strings
    -Wstrict-prototypes
    -Wold-style-definition
    -Wnested-externs
    -Wmissing-include-dirs
    -Wno-unused-result
    # this project produces a lot of warnings, just ignore them for now
    -Wno-discarded-qualifiers
    -Wno-shadow
    -Wno-sign-compare
    -Werror)

target_include_directories(
    microrl
    PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)

target_link_libraries(
    microrl
    Configuration
    muslc
    utils)
