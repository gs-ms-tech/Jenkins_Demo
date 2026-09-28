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
                echo 'Script completed successfully'
            }
        }
    }
     post {
        success {
            emailext(
                to: 'georgestephenms@gmail.com',
                subject: "Jenkins Build Successful - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build ${env.BUILD_NUMBER} completed successfully."
            )
        }

        failure {
            emailext(
                to: 'georgestephenms@gmail.com',
                subject: "Jenkins Build Failed - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build ${env.BUILD_NUMBER} has failed. Please check Jenkins console output."
            )
        }
    }
}
