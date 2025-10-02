pipeline{

    agent any

    stages{

        stage('Start Grid'){
            steps{
                bat "docker compose -f grid.yaml up -d"
            }
        }

        stage('Run Test'){
            steps{
                bat "docker compose -f test-suites.yaml up"
            }
        }
    }

    post{
        always{
            bat "docker compose -f grid.yaml down"
            bat "docker compose -f test-suites.yaml down"
            archiveArtifacts artifacts: '06-jenkins-ci-cd/01-jenkins/volumes/node/workspace/SELENIUM_DOCKER_RUNNER/output/flights-reservation/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: '06-jenkins-ci-cd/01-jenkins/volumes/node/workspace/SELENIUM_DOCKER_RUNNER/output/vendor-portal/emailable-report.html', followSymlinks: false
        }
    }
}