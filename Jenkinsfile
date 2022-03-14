pipeline{
	agent any
	stages
	{
	  stage('Checkout Source') {
      steps {
        git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/sessiondevops/test-k8.git'
       }
     }
   }
 }
