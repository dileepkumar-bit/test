pipeline {
    agent any

    stages {

        stage('Checkout') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                echo 'Checking out source code'
            }
        }

        stage('Build') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                echo 'Building application...'
                sleep(time: 5, unit: 'SECONDS')
            }
        }

        stage('Run Tests in Parallel') {
            when {
                not {
                    branch 'master'
                }
            }
            parallel {

                stage('Unit Test') {
                    steps {
                        sh 'chmod +x tests/unit-test.sh'
                        sh './tests/unit-test.sh'
                    }
                }

                stage('Integration Test') {
                    steps {
                        sh 'chmod +x tests/integration-test.sh'
                        sh './tests/integration-test.sh'
                    }
                }

                stage('UI Test') {
                    steps {
                        sh 'chmod +x tests/ui-test.sh'
                        sh './tests/ui-test.sh'
                    }
                }
            }
        }

        stage('Approval') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                input message: 'Approval of Deployment?', ok: 'Approve'
            }
        }

        stage('Deploy') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                echo 'Application Deployed Successfully'
            }
        }
    }
}
