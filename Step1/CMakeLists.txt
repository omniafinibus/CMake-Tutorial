# Set the minimum required version of CMake to be 3.10
cmake_minimum_required(VERSION 3.10)

# Create a project named Tutorial
project(Tutorial VERSION 1.0)

# Set CXX compiler standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Configure and copy TutorialConfig.h.in to TutorialConfig.h
configure_file(TutorialConfig.h.in TutorialConfig.h)

# Add an executable called Tutorial to the project
add_executable(Tutorial tutorial.cxx)

# Include ${PROJECT_BINARY_DIR}
target_include_directories(Tutorial PUBLIC ${PROJECT_BINARY_DIR})