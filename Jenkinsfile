pipeline {
    agent any
    tools {
        maven 'Maven-3.8.8'  // Name you gave in Jenkins tools config
    }
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
                echo "Deploying on main branch..."
            }
        }
    }
    post {
        always {
            echo "Pipeline finished. BUILD_NUMBER=${env.BUILD_NUMBER}, BRANCH=${env.BRANCH_NAME}"
        }
    }
}
