pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Samuelmkchoy/studentAttendance1'
            }
        }

        stage('Build') {
            steps {
                script {
                    def gradleHome = tool 'Gradle'
                    def gradle = "${gradleHome}/bin/gradle"
                    sh "${gradle} clean build"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def gradleHome = tool 'Gradle'
                    def gradle = "${gradleHome}/bin/gradle"
                    sh "${gradle} test"
                }
            }
        }
    }

    post {
        success {
            junit '**/build/test-results/test/*.xml' // Collect JUnit test results
            echo 'Build and test successful! Add additional steps as needed.'
        }
        failure {
            junit '**/build/test-results/test/*.xml' // Collect JUnit test results
            echo 'Build or test failed. Take necessary actions.'
        }
    }
}
