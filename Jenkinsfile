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
    stage("Quality Gate") {
        steps {
            timeout(time: 1, unit: 'HOURS') {
                // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                // true = set pipeline to UNSTABLE, false = don't
                // Requires SonarQube Scanner for Jenkins 2.7+
                waitForQualityGate abortPipeline: true
            }
        }
    }    
}