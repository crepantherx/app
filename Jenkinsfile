pipeline {
    agent any
    stages {
	    stage('Build') {
		steps {
		    	script {  
				sh "docker build -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT} ."
		    	}
		}
	    }

	    stage('Deploy'){
		steps {
			script {  
				docker.withRegistry('https://http://10.64.140.44/', 'jfrog') {
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT}"
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest"
				}
			}
		}
	    }
    }
}
