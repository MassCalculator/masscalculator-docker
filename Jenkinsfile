pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Docker Build') {
            steps {
                sh 'sudo ./daemon/build_docker_masscalculator.sh'
            }
        }
        stage('Docker Run') {
            steps {
                sh 'sudo ./daemon/run_docker_masscalculator.sh'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy stage is in progress'
            }
        }
    }
}
