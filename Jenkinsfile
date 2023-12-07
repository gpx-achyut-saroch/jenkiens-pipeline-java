pipeline {
    agent  any
        tools {
            maven 'Maven 3.3.9'
            jdk 'jdk17'
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