# Dockerfile for MassCalculator

# Base image
FROM ubuntu:22.04

# Install required packages
RUN apt-get update && \
	apt-get install -y build-essential cmake git sudo && \
	rm -rf /var/lib/apt/lists/*

# Clone the MassCalculator Core repository
RUN git clone https://github.com/MassCalculator/masscalculator-core.git

# Set the working directory
WORKDIR /masscalculator-core

# Checkout the latest version of the code
RUN git checkout devel

# Run the essentials script
RUN sudo tools/installers/essentials.sh

# Build the MassCalculatorCore library
RUN cmake -DBUILD_RELEASE=ON -DBUILD_TESTS=ON -Bbuild/MassCalculatorCore-Release -H. && \
	cmake --build build/MassCalculatorCore-Release

# Set the entrypoint command to run the MassCalculator. Currently running tests until other projects are added
ENTRYPOINT ["/bin/bash", "-c", "cd build/MassCalculatorCore-Release && ctest"]
