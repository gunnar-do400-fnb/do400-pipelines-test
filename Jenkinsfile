node('nodejs') {
    stage('Checkout') {
        git branch: 'master', url: https://github.com/gunnar-do400-fnb/do400-pipelines-test.git
    }
    stage('Backend Tests') {
        sh 'node ./backend/test.js'
    }
    stage('Frontend Tests') {
        sh 'node ./frontend/test.js'
    }
}