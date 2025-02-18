pipeline {
  agent any

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
    stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }   
    }
}
