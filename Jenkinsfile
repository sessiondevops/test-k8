def valuepod(){
	def mdconf = readYaml file: "pod-deletetest.yaml"
	return mdconf; 
}
pipeline{
	agent any
	stages
	{
	  stage('Checkout Source') {
      steps {
        git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/sessiondevops/test-k8.git'
	      script {
	      	mdconf = valuepod()
		wflow = println mdconf.metadata.name
		println wflow
	      }
       }
     }
   }
 }
