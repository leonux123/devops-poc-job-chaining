pipeline {
    agent any
    stages {
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                bat 'echo Starting DEV deploy...'
		    	     build job: 'Dev_job'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
            }
        }
        stage('Deliver for release') {
            when {
                branch 'release'  
            }
            steps {
                bat 'echo Starting ITG deploy...'
	                     build job: 'ITG_job'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
            }
        }
	stage('Deploy to PROD') {
            when {
                branch 'master' 
            }
            steps {
		    bat 'echo Starting PROD deploy...'
		    	     bat 'bash'         
		    	     bat 'ssh -i /c/Users/larias6/.ssh/MyKeyPair.pem ec2-user@34.215.225.240 ./kill.sh'
            }
        }
    }
}
