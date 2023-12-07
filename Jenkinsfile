pipeline {
    agent {
        docker {
            image 'maven:3.9.5-eclipse-temurin-17-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Sonar') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=sqp_6dbf1775f81a36a026b76854f5a2b6b7b696ff95'
            }
        }
    }
}