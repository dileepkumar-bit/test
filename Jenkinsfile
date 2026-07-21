pipeline {
  agent any 

  stages { 

    stage('Checkout') {
       steps {
           echo 'Checking out source code...'
       }
    }

    stage('Build') {
        steps {
           echo 'Building application...'
       }
    }

    stage('Unit Test') {
      steps { 
        echo 'Running Tests.....'
      }
    }
      
    stage('Approval') {
      steps { 
        input message: 'Deploy to Production?', ok: 'Approve'
      }
    }
      
    stage('Deploy To Production') {
        steps {
            echo 'Deploying application....'
        } 
      } 
    }
  }
