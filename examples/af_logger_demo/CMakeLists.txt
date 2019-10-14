cmake_minimum_required (VERSION 2.8)

set(AFLIB_DIR ${CMAKE_SOURCE_DIR}/../..)

# Set this to the right profile for the device you're using
set(PROFILE_INCLUDE_DIR ${AFLIB_DIR}/examples/af_logger_demo/profile/af_logger_demo_Plumo-2D_UART)

project (af_logger_demo)

include_directories(${AFLIB_DIR} ${PROFILE_INCLUDE_DIR} . )

add_subdirectory(${AFLIB_DIR} AFLIB)

add_executable(af_logger_demo af_logger_demo.c)

if (DARWIN)
    FIND_LIBRARY(COREFOUNDATION_LIBRARY CoreFoundation)
endif (DARWIN)

target_link_libraries(af_logger_demo afLib ${COREFOUNDATION_LIBRARY})
