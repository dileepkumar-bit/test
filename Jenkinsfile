pipeline {
    agent any

    stages {

        stage('Branch Check') {
            steps {
                script {
                    echo "Current Branch: ${env.BRANCH_NAME}"

                    if (env.BRANCH_NAME == "master") {
                        currentBuild.result = 'NOT_BUILT'
                        error("Master branch detected. Skipping pipeline.")
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

        // Remaining stages...
    }
}
