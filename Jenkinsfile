pipeline{
	agent any
	parameters {
		choice(
			name: 'ENVIRONMENT',
			choices: ['QA', 'Dev', 'PROD'],
			description: 'select deployment environment'
		)
	}
	stages {
		stage('env_print') {
			steps{
				echo "this deployment is for ${params.ENVIRONMENT}"
			}
		}
		stage('pull_image') {
			steps{
				sh '''
				docker pull node:lts-alpine3.22
				docker image ls
				'''
			}
		}
	}
}
