pipeline {
    agent any
    stages {
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                sh 'Starting DEV deploy..."'
		    	     build "Dev_job"
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
	            	     bat 'bash'         
		    	     bat 'ssh -i /c/Users/larias6/.ssh/MyKeyPair.pem ec2-user@34.219.45.91 ./kill.sh'
            }
        }
        stage('Deliver for release') {
            when {
                branch 'release'  
            }
            steps {
                sh 'Starting ITG deploy..."'
	                     build "ITG_job"
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     bat 'bash'         
		    	     bat 'ssh -i /c/Users/larias6/.ssh/MyKeyPair.pem ec2-user@34.221.96.160 ./kill.sh'
            }
        }
	stage('Deploy to PROD') {
            when {
                branch 'master' 
            }
            steps {
                sh 'Starting PROD deploy..."'
	                     build "PROD_job"
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     bat 'bash'         
		    	     bat 'ssh -i /c/Users/larias6/.ssh/MyKeyPair.pem ec2-user@34.219.125.64 ./kill.sh'
            }
        }
    }
}
