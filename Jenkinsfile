pipeline {
    agent any
    stages {
        stage("build & SonarQube analysis") {
          node {
              def scannerHome = tool 'SonarQube Scanner 2.8';
              withSonarQubeEnv('My SonarQube Server') {
              sh "${scannerHome}/bin/sonar-scanner"
          }
        }
    }
}