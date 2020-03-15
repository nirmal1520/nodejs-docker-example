//Nirmal testing

pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
        stage('Deploy Docker Image'){
      
      // deploy docker image to nexus

     // echo "Docker Image Tag Name: ${dockerImageTag}"
      
      //withCredentials([usernamePassword(credentialsId: 'ecr', passwordVariable: 'pass', usernameVariable: 'user')]) {
       
      docker.withRegistry("https://807410046616.dkr.ecr.us-east-1.amazonaws.com", "ecr:us-east-1:aws") {
	      
      def customImage = docker.build("nodejs-docker-example:${env.BUILD_ID}")
                  customImage.push()

     // docker.image("${dockerImageTag}").push()
             }
	}
    }
}
