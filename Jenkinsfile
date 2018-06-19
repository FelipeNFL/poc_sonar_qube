node {  
    stage('Build') { 
        def scannerHome = tool 'SonarQube Scanner 2.8';
        withSonarQubeEnv('My SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
        } 
    }
    stage('Test') { 
        // 
    }
    stage('Deploy') { 
        // 
    }
}