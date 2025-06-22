pipeline {
    agent any

    tools {
        maven 'maven-3'
    }

    environment {
        GIT_REPO = 'https://github.com/rushi-admin/spring-boot-spring-security-jwt-authentication.git'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: "${env.GIT_REPO}"
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
