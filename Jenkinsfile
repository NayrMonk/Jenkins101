pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to build')
        string(name: 'BUILD_ENV', defaultValue: 'dev', description: 'Build environment')
    }

    environment {
        NEW_VERSION = "1.3.0"
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version ${NEW_VERSION} on branch ${params.BRANCH_NAME}"
                // Uncomment this line to actually build
                // bat "mvn clean package -Dversion=${NEW_VERSION}"
            }
        }

        stage('Unit Test') {
            when {
                expression { return params.BUILD_ENV == 'dev' }
            }
            steps {
                echo 'Running unit tests...'
                // Add: bat "mvn test" if needed
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment commands here
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            // deleteDir() // Uncomment if you want to clean workspace after build
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
