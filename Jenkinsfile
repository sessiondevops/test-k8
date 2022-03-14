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
		        //println mdconf.metadata.name
		        test = mdconf.metadata.name
		        println test
		        sh """
		            sed -i "s/$test/$test-${BUILD_NUMBER}/g" pod-deletetest.yaml
		            cat pod-deletetest.yaml
		        """
	      }
       }
     }
     stage('workflow') {
        withCredentials([file(credentialsId: 'k8-config', variable: 'KUBECONFIG')]) {
            sh 'kubectl config view'
            }
        }
    }
}
