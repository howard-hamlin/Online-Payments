library 'cdd-global-pipeline-libraries'
properties([
 pipelineTriggers([githubPush()]),
 parameters([
   string(defaultValue: 'http://ibndev003773.bpc.broadcom.net:8080', description: '', name: 'CDD_SERVER_URL', trim: true),
   string(defaultValue: '00000000-0000-0000-0000-000000000000', description: '', name: 'CDD_TENANT_ID', trim: true)])
 ])
params.each { k, v -> env[k] = v }
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
  
  freeStyleJob('NexusArtifactUploaderJob') {
    steps {
      nexusArtifactUploader {
        nexusVersion('nexus2')
        protocol('http')
        nexusUrl('ibndev003773.bpc.broadcom.net:8080/nexus')
        groupId('dummy')
        version('1.0')
        repository('NatWest-Online-Payments')
        credentialsId('44620c50-1589-4617-a677-7563985e46e1')
        artifact {
            artifactId('dummy')
            type('war')
            classifier('')
            file('build/libs/dummy.war')
        }
      }
    }
}


  
 }
 post {
  success {
    sendNotificationToCDDCall projectName: 'NatWest', scope: 'BUSINESS_APPLICATION', businessApplicationName: 'NatWest Biometric Payment'
  }
 }
}
