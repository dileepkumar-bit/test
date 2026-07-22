pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                script {
                    try {
                        // Deployment logic
                        deployToEnvironment('production')

                    } catch (Exception e) {
                        echo "Deployment failed: ${e.getMessage()}"

                        // Rollback logic
                        rollbackToPreviousDeployment('production')

                        // Mark build as failed after rollback
                        error("Deployment failed. Rollback completed.")
                    }
                }
            }
        }
    }
}

def deployToEnvironment(environment) {
    echo "Deploying application to ${environment}"

    // Simulating deployment failure for testing
    error("Application deployment failed intentionally")
}

def rollbackToPreviousDeployment(environment) {
    echo "Starting rollback in ${environment}"

    // Simulating rollback process
    echo "Restoring previous stable version"

    echo "Rollback completed successfully"
}
