pipeline{
	agent any
	stages
	{
	  stage('Checkout Source') {
      steps {
        git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/sessiondevops/test-k8.git'
	      script {
	      	def conf = readYaml file: "pod-deletetest.yaml"
		echo conf.metadata
	      }
       }
     }
   }
 }
