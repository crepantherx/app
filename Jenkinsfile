pipeline {
    agent any
    stages {
	    stage('Build') {
		steps {
		    	script {  
				sh "docker build -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${env.BUILD_ID} -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest -t crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT} ."
		    	}
		}
	    }
	    stage('Test') {
		steps {
		    	script {  
				sh "echo 'Testing'"
		    	}
		}
	    }
	    stage('Staging') {
		steps {
		    	script {  
				docker.withRegistry('https://crepantherx.jfrog.io', 'jfrog') {
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${GIT_COMMIT}"
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:latest"
					sh "docker push crepantherx.jfrog.io/techmahindra-docker-dev-local/notes:${env.BUILD_ID}"
				}
		    	}
		}
	    }
	    stage('Production'){
		steps {
			script {  
				sh "echo 'Staging'"
			}
		}
	    }
    }
}
