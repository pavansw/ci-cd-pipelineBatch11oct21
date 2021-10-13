pipeline {
  agent any
  stages {
    stage('SCM for Java Code') {
      steps {
        git(url: 'https://github.com/pavansw/simpleMavenJunit.git', branch: 'master', poll: true)
        echo 'Polling to Developers SCM'
      }
    }

    stage('Maven Compile') {
      steps {
        sh '''mvn clean
mvn compile'''
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        sh 'echo "TEsting is dome"'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Publish TestResult') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Execute') {
      steps {
        sh 'java -jar target/*.jar'
      }
    }

  }
}