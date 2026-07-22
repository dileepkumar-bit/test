pipeline {
    agent any

    stages {

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

           stage('unit test') {
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

   stage ('Approval') {
       steps {
         input message: 'Approval For Deployment?', ok: 'Approve'
       }
   }  
   stage('Deploy') {
    steps {
     echo 'Application Deployed Successfully in website'

        }
     }
   }
 }
