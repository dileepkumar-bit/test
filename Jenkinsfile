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

                        // Mark the build as failed
                        error("Deployment failed. Rollback completed.")
                    }
                }
            }
        }
    }
}

def deployToEnvironment(environment) {
    // Deployment code specific to the environment
    echo "Deploying to ${environment}"

    // Example:
    // sh "scp app.war user@server:/opt/tomcat/webapps/"
    // sh "ssh user@server 'systemctl restart tomcat'"
}

def rollbackToPreviousDeployment(environment) {
    // Rollback code specific to the environment
    echo "Rolling back deployment in ${environment}"

    // Example:
    // sh "scp backup/app.war user@server:/opt/tomcat/webapps/"
    // sh "ssh user@server 'systemctl restart tomcat'"
}
