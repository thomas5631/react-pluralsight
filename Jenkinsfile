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
        stage('getEnv') {
          environment {
            THIS_ENV_VAR = 'this_is_an_env_var'
          }
          steps {
            sh 'echo $THIS_ENV_VAR'
          }
        }
    }
    post {
        always {
          junit 'test-results.xml'
          echo 'Cleaning up workspace'
          deleteDir()
        }
        success {
            mail to: 'thomaslilley1@live.co.uk',
                 subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Yay for ${env.BUILD_URL}"
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
