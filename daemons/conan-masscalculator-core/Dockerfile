# Dockerfile for Conan MassCalculator Core

## Base image
FROM ubuntu:22.04

## Install required packages
RUN apt-get update && \
	apt-get install -y build-essential cmake git sudo && \
	rm -rf /var/lib/apt/lists/*

## Clone the Conan MassCalculator Core repository
RUN git clone https://github.com/MassCalculator/conan-masscalculator-core.git

## Set the working directory
WORKDIR /conan-masscalculator-core

## Checkout the latest version of the code
RUN git checkout master

## Run the essentials script
RUN sudo tools/installers/essentials.sh

## Detect Conan Profile
RUN conan profile detect

## Create conan package
RUN conan create all/ --version 0.1.0 --user masscalculator --channel stable --build missing

## Set the entrypoint command to run the MassCalculator. Currently running tests until other projects are added
ENTRYPOINT ["/bin/bash", "-c", "cd all/test_package/build/gcc-11-x86_64-gnu17-release && ./PackageTest"]
