pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				
				git clone https://github.com/maghamkishore/sample-node-project.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				
				cd sample-node-project
				sudo docker build -t kish24/nodejs:1.0 .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push kish24/nodejs:1.0
                sudo docker run -d -p 8083:3005 --name samplenode1 kish24/nodejs:1.0
                sudo docker ps
                '''
            }
        }
    }
}