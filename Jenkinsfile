pipeline {
    agent any

    stages {
        stage('CI Check') {
            steps {
                echo 'CI pipeline is running'
		}
            }

	stage('Docker Build') {
	     steps {
	            bat 'Docker build -t ci-cd-demo .'

            }
        }

	stage('Docker run') {
	steps {
	    bat 'docker run ci-cd-demo'
	    }

	   } 
    }
}

