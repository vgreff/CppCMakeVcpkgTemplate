# CMakeLists.txt
cmake_minimum_required(VERSION 3.26)
project(cpp_template)

# Find dependencies provided by vcpkg (via vcpkg.cmake)
find_package(unofficial-sqlite3 CONFIG REQUIRED)
find_package(fmt CONFIG REQUIRED)

# main target
add_executable(main)
target_sources(main PRIVATE src/main.cpp)
target_link_libraries(main PRIVATE unofficial::sqlite3::sqlite3 fmt::fmt-header-only)
set_property(TARGET main PROPERTY CXX_STANDARD 23)

# vgmain target
add_executable(vgmain)
target_sources(vgmain PRIVATE src/vgmain.cpp)
target_link_libraries(vgmain PRIVATE unofficial::sqlite3::sqlite3 fmt::fmt-header-only)
set_property(TARGET vgmain PROPERTY CXX_STANDARD 23)

# tests target
add_executable(tests)
target_sources(tests PRIVATE src/test.cpp)
target_link_libraries(tests PRIVATE unofficial::sqlite3::sqlite3 fmt::fmt-header-only)
set_property(TARGET tests PROPERTY CXX_STANDARD 23)

enable_testing()
add_test(tests tests)