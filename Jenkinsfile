pipeline {
    agent any{ 
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh "sudo docker-compose build"
                
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

        stage('Container Up') {
            steps {
                echo 'Docker container up'
                sh "sudo docker-compose up -d"
            }
        }
    }
}
