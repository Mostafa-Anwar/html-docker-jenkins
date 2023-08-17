pipeline {
    agent {
        label 'docker'
    }
    
    stages {
        stage('grab-code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master'], [[name: '*/feat/add-blaa']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Mostafa-Anwar/simple-html-app.git']]])            }
        }
        
        stage('build-image') {
            steps {
                sh "docker build -t jenkins-demo:${BUILD_NUMBER} ."
            }
        }

        stage('tag-image') {
            steps {
                sh "docker tag jenkins-demo:${BUILD_NUMBER} jenkins-demo:latest"
            }
        }
        
        stage('run-container-from-image') {
            steps {
                sh "docker run -d -p 80:80 jenkins-demo:${BUILD_NUMBER}"
            }
        }
    }
}
