pipeline {
    agent any

    stages {
        stage('Sonar Quality Status') {
            agent {
                docker {
                    image 'maven:3.9.6-eclipse-temurin-17' // or any latest Maven image
                    args '-v /var/lib/jenkins/.m2:/root/.m2'
                }
            }
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}

