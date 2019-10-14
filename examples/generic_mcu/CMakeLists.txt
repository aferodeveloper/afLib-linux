cmake_minimum_required (VERSION 3.2)

set(AFLIB_DIR ${CMAKE_SOURCE_DIR}/../..)

project (generic_mcu)

include_directories(${AFLIB_DIR} . )

add_subdirectory(${AFLIB_DIR} AFLIB)

add_executable(generic_mcu generic_mcu.c)

if (DARWIN)
    FIND_LIBRARY(COREFOUNDATION_LIBRARY CoreFoundation)
endif (DARWIN)

target_link_libraries(generic_mcu afLib ${COREFOUNDATION_LIBRARY})
