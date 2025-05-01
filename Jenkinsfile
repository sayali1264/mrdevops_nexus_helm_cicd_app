pipeline {
    agent any

    stages {
        stage('Sonar Quality Status') {
            agent {
                docker {
                    image 'maven'
                    args '-v $HOME/.m2:/root/.m2' // Mount host .m2 to container
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
