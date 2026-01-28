pipeline{
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

	stage('Deploy') {
	steps {
	    bat
	    '''docker stop ci-cd-container || echo not running
        docker rm ci-cd-container || echo not present
        docker run --name ci-cd-container ci-cd-demo
	'''
	    }

	   } 
    }
}

