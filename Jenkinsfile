pipeline {
    agent any

    stages {
        stage("checkout") {
            steps {
                git branch:'main', url: 'https://github.com/AndreiTeodorPop/jenkins-spring-petclinic.git'
            }
        }
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
