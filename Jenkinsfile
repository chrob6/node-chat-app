pipeline{
  any stage
  
  stages{
    stage('Build') {
	  sh 'npm install'
	  echo 'Start Building..'
    }
    stage('Test') {
	  sh 'npm run test'
	  echo 'Start Testing..'
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
