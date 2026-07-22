pipeline {
    agent any

    stages {

        stage('Branch Check') {
            steps {
                script {
                    echo "BRANCH_NAME = ${env.BRANCH_NAME}"
                    echo "GIT_BRANCH = ${env.GIT_BRANCH}"
                    echo "JOB_NAME = ${env.JOB_NAME}"

                    // Skip if current branch is master
                    if (env.BRANCH_NAME == "master") {
                        currentBuild.result = 'NOT_BUILT'
                        echo "Master branch detected. Skipping pipeline."
                        return
                    }
                }
            }
        }

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sleep(time: 5, unit: 'SECONDS')
            }
        }

        stage('Run Tests in Parallel') {
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
            steps {
                input message: 'Approval of Deployment?', ok: 'Approve'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application Deployed Successfully'
            }
        }
    }
}
