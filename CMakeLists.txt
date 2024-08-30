cmake_minimum_required(VERSION 3.10)

# Set the project name and version
project(VulkanTest VERSION 1.0)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Set the optimization level
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

# Add the executable
add_executable(VulkanTest main.cpp)

# Find the Vulkan package
find_package(Vulkan REQUIRED)

# Find the GLFW package
find_package(glfw3 REQUIRED)

# Add system libraries (Linux specific)
find_library(LIBDL dl)
find_library(LIBPTHREAD pthread)
find_library(LIBX11 X11)
find_library(LIBXXF86VM Xxf86vm)
find_library(LIBXRANDR Xrandr)
find_library(LIBXI Xi)

# Link libraries to the executable
target_link_libraries(VulkanTest PRIVATE Vulkan::Vulkan glfw ${LIBDL} ${LIBPTHREAD} ${LIBX11} ${LIBXXF86VM} ${LIBXRANDR} ${LIBXI})
