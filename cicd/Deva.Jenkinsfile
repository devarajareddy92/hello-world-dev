
pipeline {
  agent any
  tools{
  maven 'maven-3.6.3'
  }
  options {
    disableConcurrentBuilds()
    disableResume()
    buildDiscarder(logRotator(numToKeepStr: '10'))
    timeout(time: 1, unit: 'HOURS')
  }
  parameters {
    string(name: 'MAVEN_GOAL', defaultValue: 'compile', description: 'Maven goal eg: compile, test, package or install')
  }
  stages {
    stage ('Build') {
      steps {
        sh "mvn clean ${params.MAVEN_GOAL}"
      }
    }
  }
  post {
    always {
      deleteDir()
    }
  }
}
