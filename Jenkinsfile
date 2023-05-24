pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Environment setup') {
            steps {
                sh "sudo tools/installers/essentials.sh"
            }
        }
        stage('Configure CMake') {
            steps {
                sh "cmake -B build/masscalculator-docker-Release -G Ninja -DCMAKE_BUILD_TYPE=Release"
            }
        }
        stage('Docker Build') {
            parallel {
                stage('masscalculator-cli') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t build-masscalculator-cli-docker --config Release"
                    }
                }
                stage('masscalculator-core') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t build-masscalculator-core-docker --config Release"
                    }
                }
                stage('masscalculator-gui') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t build-masscalculator-gui-docker --config Release"
                    }
                }
                stage('masscalculator-yocto') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t build-masscalculator-yocto-docker --config Release"
                    }
                }
            }
        }
        stage('Docker Run') {
            parallel {
                stage('masscalculator-cli') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t run-masscalculator-cli-docker --config Release"
                    }
                }
                stage('masscalculator-core') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t run-masscalculator-core-docker --config Release"
                    }
                }
                stage('masscalculator-gui') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t run-masscalculator-gui-docker --config Release"
                    }
                }
                stage('masscalculator-yocto') {
                    steps {
                        sh "sudo cmake --build build/masscalculator-docker-Release -t run-masscalculator-yocto-docker --config Release"
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy stage is in progress'
            }
        }
    }
}
