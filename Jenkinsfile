pipeline {
    agent any
    stages {
        stage('SonarQube analysis') {
                steps {
                    def scannerHome = tool 'SonarQube Scanner 2.8';
                    withSonarQubeEnv('My SonarQube Server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}