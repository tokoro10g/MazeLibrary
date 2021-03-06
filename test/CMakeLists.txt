## author: Ryotaro Onuki <kerikun11+github@gmail.com>

# GoogleTest Project
# see https://github.com/google/googletest/blob/master/googletest/README.md
# Download and unpack googletest at configure time
configure_file(./googletest-download.cmake googletest-download/CMakeLists.txt)
execute_process(COMMAND ${CMAKE_COMMAND} -G "${CMAKE_GENERATOR}" .
  RESULT_VARIABLE result
  WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/googletest-download )
if(result)
  message(FATAL_ERROR "CMake step for googletest failed: ${result}")
endif()
execute_process(COMMAND ${CMAKE_COMMAND} --build .
  RESULT_VARIABLE result
  WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/googletest-download )
if(result)
  message(FATAL_ERROR "Build step for googletest failed: ${result}")
endif()

# Prevent overriding the parent project's compiler/linker
# settings on Windows
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

# Add googletest directly to our build. This defines
# the gtest and gtest_main targets.
add_subdirectory(${CMAKE_CURRENT_BINARY_DIR}/googletest-src
                 ${CMAKE_CURRENT_BINARY_DIR}/googletest-build
                 EXCLUDE_FROM_ALL)

# The gtest/gtest_main targets carry header search path
# dependencies automatically when using CMake 2.8.11 or
# later. Otherwise we have to add them here ourselves.
if (CMAKE_VERSION VERSION_LESS 2.8.11)
  include_directories("${gtest_SOURCE_DIR}/include")
endif()

## test mazelib
include_directories(${CMAKE_HOME_DIRECTORY}/include)
file(GLOB SRCS *.cpp)
add_executable(test_gtest ${SRCS})
target_link_libraries(test_gtest mazelib gtest)

add_custom_target(gt
  COMMAND ${CMAKE_CURRENT_BINARY_DIR}/test_gtest
  DEPENDS test_gtest mazelib gtest
  WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
)
