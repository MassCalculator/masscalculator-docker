cmake_minimum_required(VERSION 3.15)

################################################################################
#
# Project definition
#
################################################################################

# Define the project
project(masscalculator-docker
        VERSION 0.1.0
        HOMEPAGE_URL "https://github.com/MassCalculator/masscalculator-docker"
        DESCRIPTION "masscalculator-docker daemons docs and build scripts"
        LANGUAGES CXX
)

################################################################################
#
# Additional CMake functionalities
#
################################################################################

# Additional CMake modules are added here to allow finding libraries not
# natively supported by CMake and to be able to include CMake files
# uder third_party/ redirectly.
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH}
  "${CMAKE_SOURCE_DIR}/third_party"
)

# Search for all third party dependencies
include(third_party)

################################################################################
#
# CMake targets definition
#
################################################################################

if(${BUILD_DOCS})
  # This adds the doxygen documentation.
  add_subdirectory(docs)
endif()

# This adds the custom targets to run the sripts for each daemon.
add_subdirectory(daemons)
