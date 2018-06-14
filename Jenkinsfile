pipeline {
    agent { docker { image 'node:9.11.2' } }
    stages {
        stage('install') {
          steps {
            sh 'npm install'
          }
        }
        stage('test') {
          steps {
            sh 'npm run test'
          }
        }
        stage('lint') {
          steps {
            sh 'npm run lint'
          }
        }
    }
    post {
        success {
            echo 'This build was successful'
        }
        failure {
            echo 'This build has failed'
        }
        unstable {
            echo 'This build was unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
