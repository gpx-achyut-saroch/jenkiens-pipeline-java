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
        stage('Test') {
            steps {
                sh 'mvn clean install sonar:sonar -Dsonar.login=sqa_f9e940c868dc31d9b5f10375faf736e41b959070'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}