# Dockerfile for MassCalculator Core

## Base image
FROM ubuntu:22.04

## Install required packages
RUN apt-get update && \
	apt-get install -y build-essential cmake git sudo && \
	rm -rf /var/lib/apt/lists/*

## Clone the MassCalculator Core repository
RUN git clone https://github.com/MassCalculator/masscalculator-core.git

## Set the working directory
WORKDIR /masscalculator-core

## Checkout the latest version of the code
RUN git checkout devel

## Run the essentials script
RUN sudo tools/installers/essentials.sh

## Build the masscalculator-core library
RUN cmake -B build/masscalculator-core-Debug -G Ninja -DCMAKE_BUILD_TYPE=Debug && \
	cmake --build build/masscalculator-core-Debug --config Debug

## Set the entrypoint command to run the MassCalculator. Currently running tests until other projects are added
ENTRYPOINT ["/bin/bash", "-c", "cd build/masscalculator-core-Debug && ctest -C Debug"]

# @todo(jimmyhalimi): Update dockerfile for proper repository, leaving as is
# for testing purposes.
