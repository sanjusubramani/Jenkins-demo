pipeline {
    agent any

    triggers {
        githubPush()
    }

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

    post {
        always {
            emailext(
                to: 'sanjusubramani2021@gmail.com',
                subject: "Build ${currentBuild.currentResult}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                mimeType: 'text/html',
                body: """
                    <h3>Build Result: ${currentBuild.currentResult}</h3>
                    <p><b>Job:</b> ${env.JOB_NAME}</p>
                    <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                    <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>

                    <h4>Console Output (last 200 lines)</h4>
                    <pre>\${BUILD_LOG, maxLines=200}</pre>
                """
            )
        }
    }
}
