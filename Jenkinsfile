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
        stage('Get Kernel') {
			steps {
				script {
					try {
						KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
					} catch(err) {
						echo "CAUGHT ERROR: ${err}"
						throw err
					}
				}
			}
		}
		stage('Say Kernel') {
			steps {
				echo "${KERNEL_VERSION}"
			}
		}
    }
	post {
		aborted {
			echo 'Why did\'t you push my button?'
		}
	}
}