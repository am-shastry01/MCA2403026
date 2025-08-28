pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Running Build..."
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running Tests..."
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying application (only on main branch)..."
                // your real deploy commands go here
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. BUILD_NUMBER=${env.BUILD_NUMBER}, BRANCH=${env.BRANCH_NAME}"
        }
    }
}
