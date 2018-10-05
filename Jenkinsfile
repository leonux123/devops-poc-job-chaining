pipeline {
    agent any
    stages {
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                sh 'Starting DEV deploy..."'
		    	     build 'Dev_job'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
	            	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@18.237.70.190 ./kill.sh'
            }
        }
        stage('Deliver for release') {
            when {
                branch 'release'  
            }
            steps {
                sh 'Starting ITG deploy..."'
	                     build 'ITG_job'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@52.43.3.218 ./kill.sh'
            }
        }
	stage('Deploy to PROD') {
            when {
                branch 'master' 
            }
            steps {
                sh 'Starting PROD deploy..."'
	                     build '.././PROD_job'
	                     input message: 'Finished using the web site? (Click "Proceed" to continue)'
		    	     sh 'ssh -i /home/leonux/aws/MyKeyPair.pem ec2-user@34.222.142.196 ./kill.sh'
            }
        }
    }
}
