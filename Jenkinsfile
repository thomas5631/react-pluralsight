pipeline {
    agent { docker { image 'node:9.11.2' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
    }
}
