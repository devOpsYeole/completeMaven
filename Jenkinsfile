pipeline {
    agent any
    tools {
        maven 'Maven-3.9.11'
    }
    stages {
        stage('Welcome Stage') {
            steps {
                echo "Welcome to Pipeline"
            }
        }
        stage('Maven Build') {
            steps {
                bat 'mvn install'
            }
        }
        stage('Build Success') {
            steps {
                echo "Build Successful"
            }
        }
    }
}
