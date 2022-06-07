pipeline {
  agent any
  tools {
    maven 'maven-3.8.3' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://104.196.152.170:8090/')], contextPath: '', onFailure: false, war: 'webapp/target/*.war' 
        }
      }
    }
  }
}
