pipeline {
    agent any

    tools {
        maven 'Maven3'   // tên Maven bạn cấu hình trong "Manage Jenkins → Global Tool Configuration"
        jdk 'JDK11'      // tên JDK bạn cấu hình trong Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/baole485-creator/devops-practice'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run') {
            steps {
                sh 'java -jar target/*.jar &'
            }
        }
    }

    post {
        success {
            echo '✅ Build & Run thành công!'
        }
        failure {
            echo '❌ Build thất bại!'
        }
    }
}
