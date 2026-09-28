pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build triggered successfully!'
                echo 'Hello from Jenkins!'
                sh 'date'
                echo 'Script completed successfully....'
            }
        }
    }

    post {
        always {
            emailext(
                to: 'georgestephenms@gmail.com',
                subject: "Jenkins Build #${BUILD_NUMBER}",
                body: """
Build completed successfully.

Job: ${JOB_NAME}
Build Number: ${BUILD_NUMBER}
Build Status: ${currentBuild.currentResult}

Please check Jenkins for more details.
"""
            )
        }
    }
}
