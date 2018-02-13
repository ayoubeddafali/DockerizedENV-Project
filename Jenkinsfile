pipeline {
  agent any
  stages {

    stage('Build') {
      steps {
        sh "mvn clean compile"
      }

    }

    stage('Unit Tests') {
      steps {
        sh 'mvn surefire:test'
        sh "mvn surefire-report:report -DoutputName=report-${env.BUILD_NUMBER}"
      }
    }

    stage('Packaging') {
      steps {
        sh "mvn clean install"
      }
    }

    stage("Sonar"){
      steps{
        sh "mvn sonar:sonar"
      }
    }
     stage('Deploy') {
      steps {
        sh "mvn clean deploy"
      }

    }

  }
}

