node {  
    stage('Scan Code') { 
        def scannerHome = tool name: 'SonarQube Scanner'
        withSonarQubeEnv('SonarQube Local') {
            sh "${scannerHome}/bin/sonar-scanner"
        } 
    }
}