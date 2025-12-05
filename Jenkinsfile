pipeline {
  agent any

  // Make sure this name matches exactly the Maven installation name
  // in Jenkins > Manage Jenkins > Global Tool Configuration
  tools {
    maven 'Maven-3.9.11'
  }

  stages {
    stage('Welcome Stage') {
      steps {
        echo "Welcome to Pipeline"
        sh 'uname -a'           // helpful diagnostic on which node we're running
      }
    }

    stage('Maven Build') {
      steps {
        // Use sh on Linux agents; -B = batch mode (CI friendly)
        sh 'mvn -B install'
      }
    }

    stage('Build Success') {
      steps {
        echo "Build Successful"
      }
    }
  }

  post {
    success {
      echo "Pipeline finished: SUCCESS"
    }
    failure {
      echo "Pipeline finished: FAILURE"
    }
    always {
      echo "Cleaning workspace..."
      cleanWs()
    }
  }
}
