pipeline {
  agent {
    docker {
      image 'maven:3-jdk-8'
    }
    
  }
  stages {
    stage('User Confimration') {
      steps {
        input 'Ready to go?'
      }
    }
    stage(' Git checkout ') {
      steps {
        git(url: 'https://github.com/mohit-kumar2/jenkins-kss.git', branch: 'mohit', credentialsId: 'acbf138db92f4000d7a04a34c36671f15c74bf33')
      }
    }
    stage('Run Test cases') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Build Artifacts ') {
      steps {
        sh 'mvn package'
      }
    }
    stage('Create and push docker image') {
      steps {
        sh 'docker '
      }
    }
  }
  post {
    always {
      archive 'target/**/*.jar'
      junit 'target/surefire-reports/*.xml'
      
    }
    
  }
}