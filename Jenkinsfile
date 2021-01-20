library 'cdd-global-pipeline-libraries'

pipeline {
 agent {
  label 'master'
 }
 stages {
  stage('Checkout') {
   steps {
    echo "***Build***"
   }
  }
 }
 post {
  success {
    sendNotificationToCDDCall projectName: 'NatWest', scope: 'BUSINESS_APPLICATION', businessApplicationName: 'NatWest Biometric Payment'
  }
 }
}
