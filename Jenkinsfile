pipeline{
  agent any
  
  stages{
    stage('Build') {
	    steps {	
	    	sh 'apt-get -y update'
		sh 'apt-get -y install git'
		sh 'apt-get install npm -y'
		sh 'git clone https://github.com/chrob6/node-chat-app'
		sh 'cd node-chat-app'
	  	sh 'npm install'
	  	echo 'Start Building..'
	    }
    }
    stage('Test') {
	    steps {
	  	sh 'npm run test'
	  	echo 'Start Testing..'
	    }
    }
    stage('Deploy') {
	    steps {
	  	echo 'Start Deploying..'
	    }
    }
  }
  post {
     failure{
    	emailext attachLog: true,
    	body: "Build no. ${env.BUILD_NUMBER}:${currentBuild.currentResult}, Job ${env.Job_NAME}",
	to:'chrobak.mar6@gmail.com',
	subject: "The pipeline failed in Jenkins"
    }
    success{
    	emailext attachLog: true,
    	body: "Build no. ${env.BUILD_NUMBER}:${currentBuild.currentResult}, Job ${env.Job_NAME}",
	to:'chrobak.mar6@gmail.com',
	subject: "The pipeline successful in Jenkins"
    }
  }  
}
