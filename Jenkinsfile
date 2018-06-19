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
        sh "cat .scannerwork/report-task.txt"
        def props = readProperties  file: '.scannerwork/report-task.txt'
        echo "properties=${props}"
        def sonarServerUrl=props['serverUrl']
        def ceTaskUrl= props['ceTaskUrl']
        def ceTask
        timeout(time: 1, unit: 'MINUTES') {
            waitUntil {
                def response = httpRequest ceTaskUrl
                ceTask = readJSON text: response.content
                echo ceTask.toString()
                return "SUCCESS".equals(ceTask["task"]["status"])
            }
        }
        def response2 = httpRequest url : sonarServerUrl + "/api/qualitygates/project_status?analysisId=" + ceTask["task"]["analysisId"], authentication: 'jenkins_scanner'
        def qualitygate =  readJSON text: response2.content
        echo qualitygate.toString()
        if ("ERROR".equals(qualitygate["projectStatus"]["status"])) {
            error  "Quality Gate failure"
        }
    }
}