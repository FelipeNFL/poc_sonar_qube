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
    stage("Quality Gate"){
        timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
            def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
            if (qg.status != 'OK') {
                error "Pipeline aborted due to quality gate failure: ${qg.status}"
            }
        }
    }
}