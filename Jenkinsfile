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

    post {
        always {
            emailext(
                to: 'your-email@gmail.com',
                subject: "Build ${currentBuild.currentResult}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                <h3>Build Result: ${currentBuild.currentResult}</h3>

                <p><b>Job:</b> ${env.JOB_NAME}</p>
                <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>

                <h4>Console Output:</h4>
                <pre>\${BUILD_LOG, maxLines=200}</pre>
                """
            )
        }
    }
}
