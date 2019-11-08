properties([pipelineTriggers([pollSCM('H/3 * * * *')])])

node(){
cleanWs()

  stage("Checkout"){
   checkout scm
}
stage("Build"){
   sh "make"
   sh "./main"
	}
stage("Archiver"){
   archiveArtifacts artifacts: 'main'
	}
}

