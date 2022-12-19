pipeline {
    agent any

    tools {
    maven 'maven_3_8_6'
    }
  
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Alfinshaji13/Sonar_demo']]])
            }
        }
        
       stage ('Build') {
         steps {
              bat 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('sonarqube-9.7.1') {
            bat 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
      }
    }
        
    }
}
