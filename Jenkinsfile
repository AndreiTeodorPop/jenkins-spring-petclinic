pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        stage("capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }
        }
    }

    post {
        always {
            echo "Sending mail"
        }
    }
}
