cmake_minimum_required (VERSION 2.8)

set(AFLIB_DIR ${CMAKE_SOURCE_DIR}/../..)

# Set this to the right profile for the device you're using
set(PROFILE_INCLUDE_DIR ${AFLIB_DIR}/examples/full_api_example/profile/full_api_example_Plumo-2D_UART)

project (full_api_example)

include_directories(${AFLIB_DIR} ${PROFILE_INCLUDE_DIR} . )

add_subdirectory(${AFLIB_DIR} AFLIB)

add_executable(full_api_example full_api_example.cpp debugprints.cpp attribute_db.cpp)

if (DARWIN)
    FIND_LIBRARY(COREFOUNDATION_LIBRARY CoreFoundation)
endif (DARWIN)

target_link_libraries(full_api_example afLib ${COREFOUNDATION_LIBRARY})
