pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
   stage('Nexus upload'){
        steps {
           echo 'Nexus Uploader....'
           //nexusArtifactUploader artifacts: [[artifactId: 'mavenapp', classifier: '', file: 'target/mavenapp-1.0.0.9.war', type: 'war']], credentialsId: 'nexus3', groupId: 'com.myapp', nexusUrl: '3.145.176.29:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'jenkins', version: '1.0.0.9'
            nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'target/app-4.0.0.war', type: 'war']], credentialsId: 'nexus3', groupId: 'com.mithun', nexusUrl: 'http://3.111.40.42:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'jenkins', version: '4.0.0'
     }  
   }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.7.69.150:8080')], onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
