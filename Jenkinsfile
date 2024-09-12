pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    parameters {
        booleanParam(name: "TEST_FRONTEND", defaultValue: true)
    }
    stages {
        stage('Parallel Tests') {
            parallel {
                stage('Backend Tests') {
                    steps {
                        sh 'node ./backend/test.js'
                    }
                }
                stage('Frontend Tests') {
                    when { expression { params.TEST_FRONTEND }}
                    steps {
                        sh 'node ./frontend/test.js'
                    }
                }
            }
        }
        stage('Matrix Demo') {
            matrix {
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
        stage('Deploy') {
            when {
                expression { env.GIT_BRANCH == 'origin/main' }
                beforeInput true
            }
            input {
                message 'Deploy the application?'
            }
            steps {
                echo 'Deploying ...'
            }
        }
    }
}
