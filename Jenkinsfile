echo "Starting Pipeline"

pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                sh "./mvnw package"
            }
        }

        stage("Capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                junit '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }

    post {
        always {
            echo "Sending Email Notification"
        }
    }
}
