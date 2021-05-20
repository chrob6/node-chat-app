pipeline{
  agent any
  
  stages{
    stage('Build') {
	    steps {	
		echo 'Start Building..'
		sh 'git pull origin master'
	  	sh 'npm install'
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
	     post {
     		failure{
    			emailext attachLog: true,
    			body: "The pipeline continue on Test stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Test failed!"
    		}
		success{
    			emailext attachLog: true,
    			body: "The pipeline failed on Test stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Test success!"
    		}
	    }
    }
    stage('Deploy') {
	    steps {
	  	echo 'Start Deploying...'
		sh 'docker build -t deploy -f deployment .'
	    }
	    post {
     		failure{
    			emailext attachLog: true,
    			body: "The pipeline continue on Deploy stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Deploy failed!"
    		}
		success{
    			emailext attachLog: true,
    			body: "The pipeline failed on Deploy stage",
			to:'chrobam.mar6@gmail.com',
			subject: "Deploy success!"
    		}
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
