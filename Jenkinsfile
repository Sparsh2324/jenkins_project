pipeline {
    agent any
    parameters {
        string(
            name: "project name",
            defaultValue: 'project1',
            description: 'enter the project name'
        )
        choice(
            name: 'ENVIRONMENT',
            choices: ["QA","Dev","STG","PROD"],
            description: 'select the project environment'
        )
    }
    environment {
        DOCKER_IMAGE = "nginx:mainline"
        IMAGE_NAME = "web-server"
    }
    stages {
        stage("pull docker image") {
            steps{
                sh '''
                docker pull ${DOCKER_IMAGE}
                docker image ls
                '''
            }
        }
        stage("deploy docker container") {
            steps{
                sh '''
                docker container prune -f
                docker run -itd --name ${IMAGE_NAME} ${DOCKER_IMAGE}
                '''
            }
        }
        stage("kill docker container") {
            steps{
                sh '''
                docker kill ${IMAGE_NAME}
                docker container prune -f
                docker ps -a
                '''
            }
        }
    }
    post {
        always {
            echo "pipeline run completed"
        }
        failure {
            echo "pipeline failed"
        }
        success {
            echo "pipeline success"
        }
    }
}
