pipeline{
  agent any
  
  stages{
    stage('Build') {
	    steps {	
		sh 'sudo apt-get -y install git'
		sh 'git pull'
 		sh 'sudo apt-get install npm -y'
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
