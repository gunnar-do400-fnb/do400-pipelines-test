pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    stages {
        stage('Backend Tests') {
            sh 'node ./backend/test.js'
        }
        stage('Frontend Tests') {
            sh 'node ./frontend/test.js'
        }
    }
}
