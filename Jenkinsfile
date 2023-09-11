echo "Starting Pipeline"

pipeline {
    agent any

    stages {
        stage("Chechout Branch") {
            steps {
                git branch:'main', url:'https://github.com/makasim98/course3-jenkins-gs-spring-petclinic'
            }
        }

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
