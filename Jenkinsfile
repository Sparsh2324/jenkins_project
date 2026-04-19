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
	}
}
