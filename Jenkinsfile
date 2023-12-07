pipeline {
    agent none

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn clean install sonar:sonar -Dsonar.login=sqp_cb87607010dcefcb4369a08129257547a99bfe04'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}