cmake_minimum_required(VERSION 3.18)

message(STATUS "toolchain file:" ${CMAKE_TOOLCHAIN_FILE})

# Set the project name
project(MyProject)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)

# Tell CMake to use vcpkg for package management
# Assuming vcpkg is already integrated (e.g., by setting the VCPKG_ROOT environment variable)
#set(CMAKE_TOOLCHAIN_FILE "C:/path/to/vcpkg/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file" FORCE)

# Find the Lua package using vcpkg
find_package(Lua REQUIRED)

# Add the executable
add_executable(MyProject main.cpp)

target_include_directories(MyProject PRIVATE ${LUA_INCLUDE_DIR})
target_link_libraries(MyProject PRIVATE ${LUA_LIBRARIES})