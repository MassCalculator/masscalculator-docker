cmake_minimum_required(VERSION 3.15)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
  COMMAND docker build -t masscalculator-yocto .
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

add_custom_target(build-masscalculator-yocto-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
  COMMAND docker run --rm masscalculator-yocto
)

add_custom_target(run-masscalculator-yocto-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
)
