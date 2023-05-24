cmake_minimum_required(VERSION 3.15)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
  COMMAND docker build -t masscalculator-cli .
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

add_custom_target(build-masscalculator-cli-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-build-command
)

add_custom_command(
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
  COMMAND docker run --rm masscalculator-cli
)

add_custom_target(run-masscalculator-cli-docker
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/docker-run-command
)
