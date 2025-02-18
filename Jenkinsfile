pipeline {
    agent any

    tools {
        maven 'Maven-3.8.8'  // Make sure Maven is installed in Jenkins
        jdk 'JDK-11'         // Ensure the correct JDK version is installed
    }

    stages {
          stage('git version check') {
            steps {
              sh "git version"
             
            }
        }   
    stage('maven version check') {
            steps {
              sh "mvn -v"
             
            }
        }  
    stage('docker version check') {
            steps {
              sh "docker -v"
             
            }
        } 
        stage('Unit Tests - JUnit and JaCoCo') {
            steps {
                script {
                    try {
                        sh "mvn clean test"
                    } finally {
                        // Publish JUnit Test Results
                        junit '**/target/surefire-reports/*.xml'

                        // Publish JaCoCo Coverage Report
                        jacoco(execPattern: '**/target/jacoco.exec')
                    }
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/site/jacoco/index.html', fingerprint: true
        }
    }
}
