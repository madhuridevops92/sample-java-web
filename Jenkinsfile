pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/Ajayvarma8142/sample-java-web.git', branch: 'master', credentialsId: 'Ajayvarma8142')
      }
    }
    stage('Initialize') {
      steps {
        sh '''
                    export PATH=C:\apache-maven-3.6.0\bin
                    export M2_HOME=C:\apache-maven-3.6.0
                '''
      }
    }
    stage('Build') {
      steps {
        echo 'build'
        sh 'mvn clean test'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Tests'
          }
        }
        stage('Junit') {
          steps {
            echo 'junit tests'
            sh 'mvn test -B -Dmaven.javadoc.skip=true -Dcheckstyle.skip=true'
          }
        }
        stage('cucumber') {
          steps {
            echo 'cucumber test cases'
          }
        }
      }
    }
    stage('Dev') {
      steps {
        echo 'Dev env'
      }
    }
    stage('Staging') {
      steps {
        echo 'stage env'
      }
    }
    stage('Production') {
      steps {
        echo 'prod env'
      }
    }
  }
}
