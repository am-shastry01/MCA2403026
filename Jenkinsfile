pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        // Ensure we have the source and a branch name
        checkout scm
        echo "Checked out branch: ${env.BRANCH_NAME}"
      }
    }

    stage('Build') {
      // Runs for EVERY branch
      steps {
        echo "== BUILD (runs on all branches) =="
        // If your agent is Linux/macOS use sh; if Windows agent use bat (see notes below)
        sh 'mvn clean package -B'
      }
    }

    stage('Test') {
      steps {
        echo "== TEST (runs on all branches) =="
        // run tests (this may duplicate tests if mvn package already ran tests)
        sh 'mvn test -B'
      }
    }

    stage('Deploy') {
      // Run this stage ONLY on the main branch
      when {
        branch 'main'
      }
      steps {
        echo "== DEPLOY (only on main) =="
        // Replace this with your real deploy command (scp/kubectl/ansible etc.)
        sh 'echo "Deploying from main branch... (replace with real deploy command)"'
      }
    }
  }

  post {
    always {
      echo "Pipeline finished. BUILD_NUMBER=${env.BUILD_NUMBER}  BRANCH=${env.BRANCH_NAME}"
      // optionally archive build artifact(s) and test reports
      archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
      junit '**/target/surefire-reports/*.xml'
    }
  }
}
