pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone your Git repo
                git branch: 'main', url: 'https://github.com/aryan/git-practice.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Running Declarative Pipeline'
                sh 'cat README.md'
            }
        }
    }
}
