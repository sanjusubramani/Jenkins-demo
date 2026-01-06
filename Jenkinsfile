pipeline {
    agent any
    stages {
        stage('Execute shell script') {
            steps {
                sh '''
                    chmod +x script.sh
                    ./script.sh
                '''
            }
        }
    }
}
