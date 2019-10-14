cmake_minimum_required (VERSION 2.8)

set(AFLIB_DIR ${CMAKE_SOURCE_DIR}/../..)

# Set this to the right profile for the device you're using
set(PROFILE_INCLUDE_DIR ${AFLIB_DIR}/examples/afBlink/profile/afBlink_Plumo-2D_UART)

project (afBlink)

include_directories(${AFLIB_DIR} ${PROFILE_INCLUDE_DIR} . )

add_subdirectory(${AFLIB_DIR} AFLIB)

add_executable(afBlink afBlink.c)

if (DARWIN)
    FIND_LIBRARY(COREFOUNDATION_LIBRARY CoreFoundation)
endif (DARWIN)

target_link_libraries(afBlink afLib ${COREFOUNDATION_LIBRARY})
