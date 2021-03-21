pipeline {
    agent any
    stages {
	    stage('Build') { // build and tag docker image
		steps {
		    	script {  
				sh "docker build -t 10.64.140.44/techmahindra-docker-dev-local/notes:latest -t 10.64.140.44/techmahindra-docker-dev-local/notes:${GIT_COMMIT} ."
		    	}
		}
	    }

	    stage('Upload'){
		steps {
			script {  
				docker.withRegistry('https://http://10.64.140.44/', 'k8s-jfrog') {
					sh "docker push 10.64.140.44/techmahindra-docker-dev-local/notes:${GIT_COMMIT}"
					sh "docker push 10.64.140.44/techmahindra-docker-dev-local/notes:latest"
				}
			}
		}
	    }
    }
}
