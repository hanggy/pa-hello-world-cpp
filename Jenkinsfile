properties([pipelineTriggers([pollSCM('H/3 * * * *')])])

node(){
cleanWs()
checkout scm
sh "make"
sh "./main"
}
pipeline {
    
    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew check'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'home/pa-hello-world-cpp/main.cpp', fingerprint: true
           }
    }
}
