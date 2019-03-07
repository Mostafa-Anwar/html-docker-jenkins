node('docker-agent') {
    stage('grab-code') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/aossama/simple-html-app.git']]])
    }
    
    stage('build-image') {
        sh "docker build -t jenkins-demo:${BUILD_NUMBER} ."
    }

    stage('tag-image') {
        sh "docker tag jenkins-demo:${BUILD_NUMBER} jenkins-demo:latest"
    }
}
