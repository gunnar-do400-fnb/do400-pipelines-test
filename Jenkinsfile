pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    stages {
        stage('Backend Tests') {
            steps {
                sh 'node ./backend/test.js'
            }
        }
        stage('Frontend Tests') {
            steps {
                sh 'node ./frontend/test.js'
            }
        }
        stage('Matrix Demo') {
            axes {
                axis {
                    name 'PLATFORM'
                    values 'RHEL', 'Fedora'
                }
                axis {
                    name 'ARCH'
                    values 'x86', 'armv9'
                }
            }
            agent {
                label 'nodejs'
            }
            stages {
                stage('Backend Tests') {
                    steps {
                        sh 'node ./backend/test.js'
                    }
                }
                stage('Frontend Tests') {
                    steps {
                        sh 'node ./frontend/test.js'
                    }
                }
            }
        }
    }
}
