pipeline {
    agent any
    environment {
        MY_NAME = "Kevin"
    }
    parameters {
        string(name: 'Name', 
        defaultValue: 'whoever you are',
        description: 'Who should I say hi to?')
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
                message "Should we continue?"
            }
            steps {
                echo 'Continuing with deployment'
            }
        }
    }
}