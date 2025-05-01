pipeline {
    agent any

    stages {
        stage('Sonar Quality Status') {
            steps {
                checkout scm // make sure source code is pulled

                script {
                    docker.image('maven:3.9.6-eclipse-temurin-17').inside('-v /var/lib/jenkins/.m2:/root/.m2') {
                        withSonarQubeEnv('sonar-server') {
                            sh 'mvn clean package sonar:sonar'
                        }
                    }
                }
            }
        }
    }
}


