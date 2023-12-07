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
                sh 'mvn clean install sonar:sonar -Dsonar.login=sqa_563928249becdedf2627fd27ad041dfad00b511c'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}