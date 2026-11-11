pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                echo "Cloning repo...."
                git branch:'main',url:""
            }
        }
        stage('Compile'){
            steps{
                echo "Compiling"
                sh 'javac TestFactorial.java Factorial.java'
            }
        }
        stage('Test'){
            steps{
                echo "Testing"
                sh 'java TestFactorial'
            }
        }
        stage('Run'){
            steps{
                echo "Running"
                sh 'java Factorial'
            }
        }
        stage('Package JAR'){
            steps{
                echo "Build"
                sh 'jar cfm factorial.jar mainfest.txt Factorial.class'
            }
        }
        stage('Archive JAR'){
            steps{
                echo "Deploy"
                archiveArtifacts artifacts: 'factorial.jar'
            }
        }
    }
post{
    success{
        echo "Pipeline successful!"
    }
    failure{
        echo 'Pipeline failed'
    }
}
}