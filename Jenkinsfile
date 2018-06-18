pipeline {
    agent any
    stages {
        stage('SCM') {
            git 'https://github.com/FelipeNFL/poc_sonar_qube'
        }
        stage('SonarQube analysis') {
            def scannerHome = tool 'SonarQube Scanner 2.8';
            withSonarQubeEnv('My SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
            }
        }
    }
}