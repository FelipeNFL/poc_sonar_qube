node {  
    stage('Scan Code') { 
        def scannerHome = tool 'SonarQube Scanner for Jenkins 2.7.1';
        withSonarQubeEnv('My SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
        } 
    }
}