pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Pulling code from Git repository...'
                git branch: 'main', url: 'https://github.com/gs-ms-tech/Jenkins_Demo.git'
            }
        }

        stage('Run Script') {
            steps {
				echo 'Executing Script...'
				sh 'chmod +x demo.sh'
                sh './demo.sh'
                echo 'Script completed successfully....'
            }
        }
    }
      post {
        always {
            mail(
                to: 'YOUR_EMAIL@example.com',
                subject: "Jenkins Build ${BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """
Hello,

Jenkins build has completed.

Project: ${JOB_NAME}
Build Number: ${BUILD_NUMBER}
Status: ${currentBuild.currentResult}

Git Commit: ${GIT_COMMIT}

Jenkins Build URL:
${BUILD_URL}

Regards,
Jenkins
""",
                attachLog: true
            )
        }
    }
}
