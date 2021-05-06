pipeline{
  agent any
  
  stages{
    stage('Build') {
	    steps {	
		echo 'Start Building..'
		sh 'git pull origin master'
	  	sh 'npm installl'
	  	echo 'Finish Building..'
    	}
	    post {
     		failure{
    			emailext attachLog: true,
    			body: "The pipeline continue on Build stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Build failed!"
    		}
		success{
    			emailext attachLog: true,
    			body: "The pipeline failed on Build stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Build success!"
    		}
	    }
    }
    stage('Test') {
	    steps {
		echo 'Start Testing..'
	  	sh 'npm run test'
	  	echo 'Finish Testing..'
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
	to:'chrobam.mar6@gmail.com',
	subject: "The pipeline failed in Jenkins"
    }
    success{
    	emailext attachLog: true,
    	body: "Build no. ${env.BUILD_NUMBER}:${currentBuild.currentResult}, Job ${env.Job_NAME}",
	to:'chrobam.mar6@gmail.com',
	subject: "The pipeline successful in Jenkins"
    }
  }	  
 }
