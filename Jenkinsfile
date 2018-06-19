node {
    stage('SCM') {
        git 'https://github.com/FelipeNFL/poc_sonar_qube.git'
    }
    stage('Scan Code') { 
        def scannerHome = tool name: 'SonarQube Scanner'
        withSonarQubeEnv('SonarQube Local') {
            sh "${scannerHome}/bin/sonar-scanner"
        } 
    }
}