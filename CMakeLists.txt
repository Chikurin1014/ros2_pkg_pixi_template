cmake_minimum_required(VERSION 3.8)
project(sample_package)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_add_library(sample_lib
    src/sample_lib.cpp
    include/sample_package/sample_lib.hpp
    include/sample_package/visibility_control.h
)

ament_auto_add_executable(sample_node
    src/sample_node.cpp
)

if(BUILD_TESTING)
    find_package(ament_lint_auto REQUIRED)
    # the following line skips the linter which checks for copyrights
    # comment the line when a copyright and license is added to all source files
    set(ament_cmake_copyright_FOUND TRUE)
    # the following line skips cpplint (only works in a git repo)
    # comment the line when this package is in a git repo and when
    # a copyright and license is added to all source files
    set(ament_cmake_cpplint_FOUND TRUE)
    # the following line skips the linter which checks for cmake files
    set(ament_cmake_lint_cmake_FOUND TRUE)
    # the following line skips uncrustify (replaced with clang_format)
    set(ament_cmake_uncrustify_FOUND TRUE)
    ament_lint_auto_find_test_dependencies()
endif()

ament_auto_package()
