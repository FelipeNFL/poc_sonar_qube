node {  
    stage('Scan Code') { 
        def scannerHome = tool name: 'SonarQube Scanner'
        withSonarQubeEnv('My SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
        } 
    }
}