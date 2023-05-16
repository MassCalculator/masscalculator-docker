# Build the MassCalculator Docker

The MassCalculator Docker is built using CMake, therefore two steps are needed:

## CMake Configuration

Create a build directory, anywhere but inside the source directory.
Call CMake using the following commands:

### Basic Configuration, Debug, no Extra Tools, no Tests, no Documentation

```bash
cmake -S $MASSCALCULATOR_DOCKER_SOURCE -B <BUILD DIRECTORY> -t <TARGET>
```

### Configure Build with Doxygen Documentation

```bash
cmake -S $MASSCALCULATOR_DOCKER_SOURCE -B <BUILD DIRECTORY> -t <TARGET> -DBUILD_DOCS=ON
```

## Build

From the build directory call

### Build everything

> Note: Currently in progress.

```bash
cmake --build .
```

### Old way build

```bash
cd $MASSCALCULATOR_DOCKER_SOURCE
mkdir build && cd build
cmake .. -DBUILD_TESTS=ON 
sudo cmake --build . -t <TARGET>
```

## Available targets

* build-masscalculator-core-docker
* run-masscalculator-core-docker

### Documentation

The Doxygen documentation will be available under the subdirectory `docs/html`
of your build directory. E.g., in `build/docs/html`.
