pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    matrix {
        axes {
            axis {
                name 'PLATFORM'
                values 'RHEL', 'Fedora'
            }
            axis {
                name 'ARCHITECTURE'
                value 'amd64', 'armv9'
            }
        }
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
        }
    }
}
