pipeline {
    agent any

    environment {
	    DOCKER_CREDENTIALS = credentials('Admin')
    }
    stages {
        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Admin', usernameVariable: 'Jenkins', passwordVariable: '')]) {
                echo "Building.."
                sh "sudo docker-compose build"
                }
            }
	}
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                sudo dotnet restore src/Server/Server.csproj
                '''
            }
        }
        stage('Container Down') {
            steps {
                echo 'Docker container down'
                sh "sudo docker-compose down"
            }
        }
        stage('Container Up') {
            steps {
                echo 'Docker container up'
                sh "sudo docker-compose up -d"
            }
        }
    }
}
