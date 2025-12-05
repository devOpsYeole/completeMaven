pipeline {
  agent any

  // Make sure the name here matches a Maven installation name in
  // Jenkins > Global Tool Configuration (example name: "MAVEN_HOME")
  tools {
    maven 'Maven-3.9.11'
  }

  stages {
    stage('Welcome Stage') {
      steps {
        echo "Welcome to Pipeline"
        sh 'uname -a'
      }
    }

    stage('Maven Build') {
      steps {
        // Use sh on Linux agents; -B for batch mode (less noisy)
        sh 'mvn -B clean install'
      }
    }

    stage('Run Tests') {
      steps {
        echo "Running Unit Tests"
        // Explicit test run (optional if mvn install already ran tests)
        sh 'mvn -B test'
      }
    }

    stage('Publish Test Results') {
      steps {
        // Publish JUnit XML reports from Maven Surefire/Failsafe
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Archive Artifacts') {
      steps {
        // Archive built jars so you can download from Jenkins UI
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }

    stage('Build Success') {
      steps {
        echo "Build Successful"
      }
    }
  }

  post {
    success { echo "Pipeline finished: SUCCESS" }
    failure { echo "Pipeline finished: FAILURE" }
    always {
      echo "Cleaning workspace..."
      cleanWs()
    }
  }
}



// pipeline {
//     agent any
//     tools {
//         maven 'MAVEN_HOME'
//     }
//     stages {
//         stage('Welcome Stage') {
//             steps {
//                 echo "Welcome to Pipeline"
//             }
//         }
//         stage('Maven Build') {
//             steps {
//                 bat 'mvn install'
//             }
//         }
//         stage('Build Success') {
//             steps {
//                 echo "Build Successful"
//             }
//         }
//     }
// }
