pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk   'JDK21'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Clonando repositorio...'
                git branch: 'main',
                    credentialsId: 'github-credentials',
                    url: 'https://github.com/0009ralonso/jenkins-java-demo.git'
            }
        }
        stage('Compilar') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Empaquetar') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        success { echo 'Pipeline completado con exito!' }
        failure { echo 'Pipeline fallido. Revisar logs.' }
    }
}
