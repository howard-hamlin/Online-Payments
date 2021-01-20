library 'cdd-global-pipeline-libraries'

properties([
 parameters([booleanParam(defaultValue: false, description: 'CREATE_RELEASE_ON_CDD', name: 'CREATE_RELEASE_ON_CDD'),
 string(defaultValue: 'plugins', description: '', name: 'GIRO_NAME_KEY', trim: true)])
 ])

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
