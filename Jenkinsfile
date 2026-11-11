pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out the code from GitHub repository'
                git branch: 'main',
                    url: 'https://github.com/Sree050805/Week-5.git'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the Factorial and TestFactorial programs'
                bat 'javac Factorial.java TestFactorial.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running the TestFactorial program'
                bat 'java TestFactorial'
            }
        }

        stage('Run') {
            steps {
                echo 'Running the Factorial program'
                bat 'java Factorial'
            }
        }

        stage('Package JAR') {
            steps {
                echo 'Build'
                bat 'jar cfm factorial.jar manifest.txt Factorial.class'
            }
        }

        stage('Archive JAR') {
            steps {
                echo 'Archiving the JAR file'
                archiveArtifacts artifacts: 'factorial.jar'
            }
        }
    }

    post {
        success {
            echo 'Build, test, run and JAR creation successful and artifact is ready!'
        }

        failure {
            echo 'Build or test failed'
        }
    }
}
