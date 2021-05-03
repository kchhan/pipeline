pipeline {
    agent any
    environment {
        MY_NAME = "Kevin"
    }
    parameters {
        string(
			name: 'Name', 
        	defaultValue: 'whoever you are',
        	description: 'Who should I say hi to?'
		)
    }
    
    stages {
        stage('Say Hello') {
            steps {
                // echo "Hello, ${MY_NAME}"
                echo "Hello, ${params.Name}"
                sh "java -version"
            }
        }
        stage('Deploy') {
            options {
                timeout(time: 30,
                unit: 'SECONDS')
            }
            input {
                message "Which Version?"
				ok "Deploy"
				parameters {
					choice(
						name: 'APP_VERSION',
						choices: "v1.1\nv1.2\nv1.3",
						description: "What to deploy?"
					)
				}
            }
            steps {
                echo 'Continuing with deployment'
            }
        }
    }
	post {
		aborted {
			echo 'Why did\'t you push my button?'
		}
	}
}