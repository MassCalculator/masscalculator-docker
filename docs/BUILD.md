# Dockerfile for MassCalculator

This Dockerfile generates a container that can be used to run MassCalculator. It installs all the necessary build tools and dependencies, clones the MassCalculator source code, and builds the MassCalculator library inside the container.

## Setup

To build the Docker image, navigate to the `masscalculator-docker` directory and run the following command in your terminal:

```bash
cd masscalculator-docker
sudo ./daemon/build_docker_masscalculator.sh
```

This will create a Docker image named `masscalculator`.

## Run

To run the MassCalculator inside the Docker container, navigate to the `masscalculator-docker` directory and run the following command:

```bash
sudo ./daemon/run_docker_masscalculator.sh
```

This will start a Docker container and run the MassCalculator inside it. The output of the MassCalculator will be printed to the terminal.

Note that if you make any changes to the MassCalculator source code, you'll need to rebuild the Docker image using the `build_docker_masscalculator.sh` script before running the `run_docker_masscalculator.sh` script again.
