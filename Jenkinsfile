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
        stage('Docker Build') {
            // @todo(jimmyhalimi): Add a way to build other targets also.
            steps {
                sh "cmake -B build/masscalculator-docker-Release -G Ninja -DCMAKE_BUILD_TYPE=Release"
                sh "sudo cmake --build build/masscalculator-docker-Release -t build-masscalculator-core-docker --config Release"
            }
        }
        stage('Docker Run') {
            // @todo(jimmyhalimi): Add a way to run other targets also.
            steps {
                sh "sudo cmake --build build/masscalculator-docker-Release -t run-masscalculator-core-docker --config Release"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy stage is in progress'
            }
        }
    }
}
