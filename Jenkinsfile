pipeline {
    agent any
    stages {
	    stage('Build') { // build and tag docker image
		steps {
		    	script {  
				sh "docker build -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT} ."
		    	}
		}
	    }

	    stage('Upload'){
		steps {
			script {  
				docker.withRegistry('https://crepantherx.jfrog.io', 'jfrog') {
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT}"
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest"
				}
			}
		}
	    }
    }
}
