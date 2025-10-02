pipeline{

    agent any

    stages{

        stage('Run Test'){
            steps{
                bat "docker-compose up"
            }
        }

        stage('Grid Down'){
            steps{
                bat "docker-compose down"
            }
        }
    }
}