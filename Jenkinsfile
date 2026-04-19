pipeline{
	agent any
	parameters {
		choice (
			name: 'ENVIRONMENT',
			choices: ['QA', 'Dev', 'PROD']
		)
	}
	stages {
		stage('env_print') {
			steps{
				echo "this deployment is for ${param.ENVIRONMENT}"
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
