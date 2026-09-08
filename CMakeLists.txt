cmake_minimum_required(VERSION 3.16)

project(CMakeDemo)

add_library(math_lib SHARED math.cpp)

set_target_properties(math_lib PROPERTIES
    WINDOWS_EXPORT_ALL_SYMBOLS ON
)

target_include_directories(math_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_executable(cmake_demo main.cpp)

target_compile_features(cmake_demo PRIVATE cxx_std_17)

target_link_libraries(cmake_demo PRIVATE math_lib)

enable_testing()

add_test(
    NAME CMakeDemoTest
    COMMAND cmake_demo
)
