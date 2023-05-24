# Build the MassCalculator Docker

The MassCalculator Docker is built using CMake, therefore two steps are needed:

## CMake Configuration

Create a build directory, anywhere but inside the source directory.
Call CMake using the following commands:

### Basic Configuration, Debug, no Extra Tools, no Tests, no Documentation

```bash
cmake -S $MASSCALCULATOR_DOCKER_SOURCE -B <BUILD DIRECTORY> -t <TARGET> -G Ninja -DCMAKE_BUILD_TYPE=<Debug|Release>
```

### Configure Build with Doxygen Documentation

```bash
cmake -S $MASSCALCULATOR_DOCKER_SOURCE -B <BUILD DIRECTORY> -t <TARGET> -G Ninja -DBUILD_DOCS=ON -DCMAKE_BUILD_TYPE=<Debug|Release>
```

## Build

From the build directory call

### Build targets

```bash
sudo cmake --build <BUILD DIRECTORY> -t <Target> --config <Debug|Release>
```

> Note: Sudo is needed to give permission to docker for Dockerfile build.

#### Available targets

* build-conan-masscalculator-core-docker
* run-conan-masscalculator-core-docker
* build-masscalculator-core-docker
* run-masscalculator-core-docker

## Documentation

The Doxygen documentation will be available under the subdirectory `docs/html`
of your build directory. E.g., in `build/docs/html`.
