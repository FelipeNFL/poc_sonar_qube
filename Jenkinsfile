pipeline {
    agent any
    stages {
        stage('SonarQube analysis') {
                step {
                    def scannerHome = tool 'SonarQube Scanner 2.8';
                    withSonarQubeEnv('My SonarQube Server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}