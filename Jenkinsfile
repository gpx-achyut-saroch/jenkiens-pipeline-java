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
        stage('Sonar') {
            steps {
                 sh 'mvn clean install sonar:sonar -Dsonar.login=sqp_cb87607010dcefcb4369a08129257547a99bfe04'
            }

        }
    }
}