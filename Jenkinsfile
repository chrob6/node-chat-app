pipeline{
  agent any
  
  stages{
    stage('Build') {
	    steps {
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
  }
  post {
    success{
    	emailext attachLog: true,
    	body: 'Build no. ${env.BUILD_NUMBER}:${currentBuild.currentResult}, Job ${env.Job_NAME}',
    	recipientProviders: [developers(), requestor()],
	to:'chrobak.mar6@gmail.com',
	subject: 'The pipeline successful in Jenkins: ${env.BUILD_NUMBER}:${currentBuild.currentResult},'
    }
    failure{
    	emailext attachLog: true,
    	body: 'Build no. ${env.BUILD_NUMBER}:${currentBuild.currentResult}, Job ${env.Job_NAME}',
    	recipientProviders: [developers(), requestor()],
	to:'chrobak.mar6@gmail.com',
	subject: 'The pipeline failed in Jenkins'
    }
  }  

}
