pipeline {
    agent any
    stages {
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                sh 'echo "Starting DEV deploy..."
		    	     build job: 'devops-poc-X'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
	            	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@18.237.70.190 ./kill.sh'
            }
        }
        stage('Deliver for release') {
            when {
                branch 'release'  
            }
            steps {
                sh 'echo "Starting ITG deploy..."
	                     build job: 'devops-poc-XX'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@52.43.3.218 ./kill.sh'
            }
        }
	stage('Deploy to PROD') {
            when {
                branch 'master' 
            }
            steps {
                sh 'echo "Starting PRO deploy..."
	                     build job: 'devops-poc-1'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@34.222.142.196 ./kill.sh'
            }
        }
    }
}
