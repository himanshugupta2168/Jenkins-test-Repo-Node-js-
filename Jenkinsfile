pipeline {
    agent any
    environment {
        NODE_HOME = tool 'NodeJS' // Ensure this matches Jenkins' NodeJS tool name
        PATH = "${NODE_HOME}\\bin;${env.PATH}" // Windows-style path handling
    }
    stages {
        stage('Install Dependencies') {
            steps {
                bat 'npm install --force' // Forces installation if conflicts occur
            }
        }
        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Test') {
            steps {
                bat 'npm run  test'
            }
        }
        stage('Deploy') {
            steps {
                bat 'start node index.js'
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
