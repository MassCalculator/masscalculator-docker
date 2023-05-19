cmake_minimum_required(VERSION 3.15)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
  COMMAND docker build -t masscalculator-gui .
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

add_custom_target(build-masscalculator-gui-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
  COMMAND docker run --rm masscalculator-gui
)

add_custom_target(run-masscalculator-gui-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
)
