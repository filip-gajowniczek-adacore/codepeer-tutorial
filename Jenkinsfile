pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'
            }
        }
        stage('analyze'){
            steps {
                sh 'pwd'
                sh 'codepeer -P sdc.gpr'
            }
        }
    }
}