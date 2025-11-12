pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                // Use bat for Windows
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    // JUnit reports work the same
                    junit 'target\\surefire-reports\\*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                // Use bat for your script
                bat 'C:\data\jenkins_home\workspace\Test-Task\jenkins\scripts\deliver.bat'
            }
        }
    }
}
