pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull latest code from repo
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // If you have a build step (like React/Vite)
                // sh 'npm run build'
                echo 'Build step (if needed)'
            }
        }

        stage('Deploy to Render') {
            steps {
                // Render doesn’t integrate directly with Jenkins,
                // but you can use git push to trigger redeploy.
                // Example: pushing to your GitHub repo that Render is watching.
                sh '''
                  git config user.name "Jenkins"
                  git config user.email "jenkins@example.com"
                  git add .
                  git commit -m "Deploy from Jenkins"
                  git push origin main
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
