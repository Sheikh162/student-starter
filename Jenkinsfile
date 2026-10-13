pipeline {
    agent any

    tools {
        maven 'Maven 3'
        jdk 'JDK 17'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        always {
            junit 'course-registration-app/target/surefire-reports/TEST-*.xml'
        }
        success {
            archiveArtifacts artifacts: 'course-registration-app/target/*.jar', allowEmptyArchive: false
        }
    }
}