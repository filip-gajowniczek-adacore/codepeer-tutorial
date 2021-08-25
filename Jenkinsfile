pipeline {
    agent any
    stages {
        stage('clean') {
            steps {
                sh 'echo killing existing IDE server'
                sh 'pkill codepeer || true'                
            }
        }
        stage('analyze'){
            steps {
                sh 'pwd'
                sh 'codepeer -P sdc.gpr'
            }
        }
        stage('serve') {
            steps {
                sh 'echo forking IDE server'
                sh 
                '
               	export JENKINS_NODE_COOKIE=dontKillMe
			export BUILD_ID=dontKillMe
			echo "JENKINS_NODE_COOKIE $JENKINS_NODE_COOKIE and BUILD_ID $BUILD_ID"
			codepeer -P sdc.gpr --ide-server --port=8081 -verbose 1>codepeer-ide-server-log.txt 2>&1 &
		'                
            }
        }        
    }
}
